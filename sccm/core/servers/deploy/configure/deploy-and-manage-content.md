---
title: Inhoud implementeren
titleSuffix: Configuration Manager
description: Nadat u distributiepunten voor System Center Configuration Manager installeren, moet u hier is hoe u kunt beginnen met het implementeren van inhoud op deze.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50dcca0-4419-449d-a487-73abcadf328f
caps.latest.revision: "6"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 14d2d9cfc25f7445ad6e873f1969e1ffcd522737
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="deploy-and-manage-content-for-system-center-configuration-manager"></a>Implementeren en beheren van inhoud voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u distributiepunten voor System Center Configuration Manager installeert, kunt u beginnen om inhoud te distribueren toe. Normaal gesproken inhoud overdraagt naar distributiepunten via het netwerk, maar andere opties inhoud naar de distributiepunten op te halen bestaat. Nadat de inhoud overdraagt naar een distributiepunt, kunt u bijwerken, distribueren, verwijderen en valideren van die inhoud op distributiepunten.  

##  <a name="bkmk_distribute"></a>Inhoud distribueren  
 Normaal gesproken distribueren u inhoud naar distributiepunten zodat deze beschikbaar zijn voor clientcomputers. (De uitzondering hierop is wanneer u inhoudsdistributie op aanvraag voor een specifieke implementatie.)  Wanneer u inhoud distribueert, wordt Configuration Manager slaat de inhoudsbestanden in een pakket en distribueert het pakket naar het distributiepunt. Typen inhoud die u distribueren kunt, zijn onder andere:  

-   Toepassingsimplementatietypen  

-   Pakketten  

-   Implementatiepakketten  

-   Driverpakketten  

-   Installatiekopieën van besturingssysteem  

-   Installatieprogramma's van besturingssysteem  

-   Installatiekopieën  

-   Takenreeksen  

Wanneer u een pakket maakt dat bronbestanden, zoals een toepassing implementatie type of implementatiepakket bevat, wordt de site waarop het pakket wordt gemaakt de site-eigenaar voor de pakketinhoudsbron. Configuration Manager kopieert de bronbestanden van het bronbestandspad dat u opgeeft voor het object naar de Inhoudsbibliotheek op de siteserver die eigenaar is van de pakketinhoudsbron.  Configuration Manager wordt vervolgens de gegevens gerepliceerd naar extra sites. (Zie [de Inhoudsbibliotheek](../../../../core/plan-design/hierarchy/the-content-library.md) voor meer informatie hierover.)  

Gebruik de volgende procedure om inhoud naar distributiepunten te distribueren.  

#### <a name="to-distribute-content-on-distribution-points"></a>Inhoud op distributiepunten distribueren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassingen die u wilt distribueren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** >  **pakketten**, en selecteer vervolgens de pakketten die u wilt distribueren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** >  **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u wilt distribueren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** >  **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt distribueren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** >  **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen die u wilt distribueren.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen** > **installatieprogramma's besturingssystemen**, en selecteer vervolgens de installatieprogramma's voor besturingssystemen die u wilt distribueren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopieën die u wilt distribueren.  

    -   **Takenreeksen**: Vouw **besturingssystemen** >  **Takenreeksen**, en selecteer vervolgens de takenreeks die u wilt distribueren. Hoewel takenreeksen geen inhoud bevatten, zijn deze gekoppeld aan inhoudsafhankelijkheden die worden gedistribueerd.  

        > [!NOTE]  
        >  Als u de takenreeks wijzigt, moet u de inhoud opnieuw distribueren.  

3.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren**. De Wizard inhoud distribueren wordt geopend.  

4.  Op de **algemene** pagina, Controleer of de vermelde inhoud de inhoud die u wilt distribueren, kies of u wilt dat Configuration Manager detecteert die zijn gekoppeld aan de geselecteerde inhoud en voeg de afhankelijkheden toe aan de distributie en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  U hebt de optie voor het configureren van de **gekoppelde inhoud afhankelijkheden detecteren en toevoegen aan deze distributie** instelling alleen voor het inhoudstype van de toepassing. Configuration Manager wordt automatisch geconfigureerd voor deze instelling voor takenreeksen en kan niet worden gewijzigd.  

5.  Op de **inhoud** tabblad als weergegeven, Controleer of de vermelde inhoud de inhoud die u wilt distribueren en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  De **inhoud** pagina wordt alleen weergegeven als de **gekoppelde inhoud afhankelijkheden detecteren en toevoegen aan deze distributie** instelling is geselecteerd op de **algemene** pagina van de wizard.  

6.  Op de **doel van inhoud** pagina, klikt u op **toevoegen**, kies een van de volgende handelingen uit en volg de bijbehorende stappen:  

    -   **Verzamelingen**: Selecteer **Gebruikersverzamelingen** of **Apparaatverzamelingen**, klik op de verzameling die is gekoppeld aan een of meer distributiepuntengroepen en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  Alleen de verzamelingen die gekoppeld aan een distributiepuntgroep zijn worden weergegeven. Zie voor meer informatie over het koppelen van verzamelingen aan distributiepuntgroepen [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  

    -   **Distributiepunt**: Selecteer een bestaand distributiepunt en klik vervolgens op **OK**. Distributiepunten die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    -   **Distributiepuntengroep**: Selecteer een bestaande distributiepuntgroep en klik vervolgens op **OK**. Distributiepuntgroepen die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    Wanneer u klaar bent met het toevoegen van doelen van inhoud, klikt u op **volgende**.  

7.  Op de **samenvatting** controleert u de instellingen voor de distributie voordat u doorgaat. Als u wilt de inhoud naar de geselecteerde doelen te distribueren, klikt u op **volgende**.  

8.  De **voortgang** pagina geeft de voortgang van de distributie.  

9. De **bevestiging** pagina geeft aan of de inhoud aan de punten is toegewezen. Om te bewaken de distributie van inhoud, Zie [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

##  <a name="bkmk_prestage"></a>Gebruik voorbereide inhoud  
 U kunt de inhoudsbestanden voor toepassingen en pakkettypen voorbereiden:  

-   In de Configuration Manager-console, selecteert u de inhoud die u nodig hebt en gebruik vervolgens de **maken Wizard voorbereid inhoudsbestand** voor het maken van een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud die u hebt geselecteerd bevat.  

-   U kunt vervolgens de inhoud op een siteserver, secundaire site handmatig importeren of distributiepunt.  

-   Wanneer u het voorbereide inhoudsbestand op een siteserver importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens geregistreerd in de site server-database.  

-   Wanneer u het voorbereide inhoudsbestand op een distributiepunt importeert, worden de inhoudsbestanden worden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt en een statusbericht verzonden naar de siteserver die de site informeert dat de inhoud beschikbaar op het distributiepunt is.  

**Beperkingen en overwegingen voor vooraf geplaatste inhoud:**  

-   **Wanneer het distributiepunt zich bevindt op de siteserver**, moet u het distributiepunt voor vooraf geplaatste inhoud niet inschakelen. Gebruik in plaats daarvan de procedure in [het voorbereiden van inhoud op een distributiepunt op een siteserver](#bkmk_dpsiteserver).  

-   **Wanneer het distributiepunt is geconfigureerd als een pull-distributiepunt**, moet u het distributiepunt voor vooraf geplaatste inhoud niet inschakelen. De configuratie voor voorbereide inhoud voor een distributiepunt vervangt de pull-distributiepuntconfiguratie. Een pull-distributiepunt dat is geconfigureerd voor voorbereide inhoud heeft geen pull-inhoud van brondistributiepunt en ontvangt geen inhoud van de siteserver.  

-   **De Inhoudsbibliotheek moet worden gemaakt op het distributiepunt voordat u kunt inhoud vooraf op het distributiepunt**. Inhoud distribueren via het netwerk ten minste één keer voordat u inhoud vooraf op het distributiepunt.  

-   **Wanneer u inhoud voorbereid voor een pakket met een lang pakketbronpad** (bijvoorbeeld meer dan 140 tekens), het opdrachtregelprogramma Extract Content mogelijk niet de inhoud voor dit pakket naar de Inhoudsbibliotheek uit te pakken.  

Zie voor meer informatie over het voorbereiden van inhoudsbestanden *vooraf geplaatste inhoud* in de [beheren van netwerkbandbreedte voor inhoudsbeheer](/sccm/core/plan-design/hierarchy/manage-network-bandwidth) onderwerp.  

Gebruik de volgende secties om inhoud voor te bereiden.  

###  <a name="BKMK_CreatePrestagedContentFile"></a>Stap 1: Een voorbereid inhoudsbestand maken  
 U kunt een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud die u in de Configuration Manager-console selecteert bevat. Gebruik de volgende procedure voor het maken van een voorbereid inhoudsbestand.  

##### <a name="to-create-a-prestaged-content-file"></a>Een voorbereid inhoudsbestand maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt voorbereiden:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, klikt u op **toepassingen**, en selecteer vervolgens de toepassingen die u wilt voorbereiden.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, klikt u op **pakketten**, en selecteer vervolgens de pakketten die u wilt voorbereiden.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, klikt u op **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt voorbereiden.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen die u wilt voorbereiden.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatieprogramma's besturingssystemen**, en selecteer vervolgens de installatieprogramma's voor besturingssystemen die u wilt voorbereiden.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, klikt u op **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopieën die u wilt voorbereiden.  

    -   **Takenreeksen**: Vouw **besturingssystemen**, klikt u op **Takenreeksen**, en selecteer vervolgens de takenreeks die u wilt voorbereiden.  

3.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **voorbereid inhoudsbestand maken**. Het maken van Wizard voorbereid inhoudsbestand wordt geopend.  

    > [!NOTE]  
    >  **Voor toepassingen:** Op de **Start** tabblad, in de **toepassing** groep, klikt u op **voorbereid inhoudsbestand maken**.  
    >   
    >  **Voor pakketten:** Op de **Start** tabblad, in de &lt; *PackageName*> groep, klikt u op **voorbereid inhoudsbestand maken**.  

4.  Op de **algemene** pagina, klikt u op **Bladeren**, kies de locatie voor het voorbereide inhoudsbestand, Geef een naam voor het bestand en klik vervolgens op **opslaan**. U kunt dit voorbereide inhoudsbestand op primaire siteservers, secundaire siteservers of distributiepunten gebruiken om de inhoud en metagegevens te importeren.  

5.  Selecteer voor toepassingen **alle afhankelijkheden exporteren** wilt laten Configuration Manager detecteren en toevoegen van de afhankelijkheden die zijn gekoppeld aan de toepassing voor het voorbereide inhoudsbestand. Deze instelling is standaard geselecteerd.  

6.  In **beheerderopmerkingen**, voer optionele opmerkingen in over het voorbereide inhoudsbestand en klik vervolgens op **volgende**.  

7.  Op de **inhoud** pagina, Controleer of de vermelde inhoud de inhoud die u wilt toevoegen aan het voorbereide inhoudsbestand en klik vervolgens op **volgende**.  

8.  Op de **inhoudslocaties** pagina, geeft u de distributiepunten van waaruit de inhoudsbestanden voor het voorbereide inhoudsbestand wilt ophalen. U kunt meer dan één distributiepunt de inhoud op te halen. De distributiepunten worden weergegeven in de sectie inhoudslocaties. De **inhoud** kolom wordt weergegeven hoeveel van de geselecteerde pakketten of toepassingen beschikbaar zijn op elk distributiepunt. Configuration Manager begint met het eerste distributiepunt in de lijst om op te halen van de geselecteerde inhoud en gaat vervolgens omlaag in de lijst om op te halen van de resterende inhoud vereist is voor het voorbereide inhoudsbestand. Klik op **omhoog** of **omlaag** om de prioriteitsvolgorde van de distributiepunten te wijzigen. Als de distributiepunten in de lijst niet alle geselecteerde inhoud bevatten, moet u distributiepunten toevoegen aan de lijst die de inhoud bevatten of de wizard af te sluiten, de inhoud naar ten minste één distributiepunt distribueren en vervolgens de wizard opnieuw.  

9. Op de **samenvatting** pagina, om de details te bevestigen. U kunt teruggaan naar vorige pagina's en wijzigingen aanbrengen. Klik op **volgende** om het voorbereide inhoudsbestand te maken.  

10. De **voortgang** pagina wordt weergegeven voor de inhoud die aan het voorbereide inhoudsbestand wordt toegevoegd.  

11. Op de **voltooiing** pagina, Controleer of het voorbereide inhoudsbestand is gemaakt en klik vervolgens op **sluiten**.  

###  <a name="BKMK_AssignContentToDistributionPoint"></a>Stap 2: De inhoud toewijzen aan distributiepunten  
 Nadat u het inhoudsbestand vooraf, moet u de inhoud toewijzen aan distributiepunten.  

> [!NOTE]  
>  Wanneer u een voorbereid inhoudsbestand gebruikt voor het herstellen van de Inhoudsbibliotheek op een siteserver en niet hoeft te voorbereiden van de bestanden op een distributiepunt, kunt u deze procedure overslaan.  

 Gebruik de volgende procedure om toe te wijzen de inhoud van het voorbereide inhoudsbestand naar distributiepunten.  

> [!IMPORTANT]  
>  Controleer of dat de distributiepunten die u wilt voorbereiden, zijn geconfigureerd als voorbereide distributiepunten of dat de inhoud via het netwerk naar de distributiepunten wordt gedistribueerd.  

##### <a name="to-assign-the-content-to-distribution-points"></a>De inhoud toewijzen aan distributiepunten  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende voor het type inhoud dat u hebt geselecteerd stappen bij het maken van het voorbereide inhoudsbestand:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, klikt u op **toepassingen**, en selecteer vervolgens de toepassingen die u hebt voorbereid.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, klikt u op **pakketten**, en selecteer vervolgens de pakketten die u hebt voorbereid.  

    -   **Implementatiepakketten**: Vouw **Software-Updates**, klikt u op **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u hebt voorbereid.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, klikt u op **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u hebt voorbereid.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen die u hebt voorbereid.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatieprogramma's besturingssystemen**, en selecteer vervolgens de installatieprogramma's voor besturingssystemen die u hebt voorbereid.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, klikt u op **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopieën die u hebt voorbereid.  

3.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren**. De Wizard inhoud distribueren wordt geopend.  

4.  Op de **algemene** pagina, Controleer of de vermelde inhoud de inhoud die u hebt voorbereid, kies of u wilt dat Configuration Manager detecteert die zijn gekoppeld aan de geselecteerde inhoud en voeg de afhankelijkheden toe aan de distributie en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  U hebt de optie voor het configureren van de **gekoppelde inhoud afhankelijkheden detecteren en toevoegen aan deze distributie** instelling alleen voor het inhoudstype van de toepassing. Configuration Manager wordt automatisch geconfigureerd voor deze instelling voor takenreeksen en kan niet worden gewijzigd.  

5.  Op de **inhoud** pagina, indien weergegeven, Controleer of de vermelde inhoud de inhoud die u wilt distribueren en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  De **inhoud** pagina wordt alleen weergegeven als de **gekoppelde inhoud afhankelijkheden detecteren en toevoegen aan deze distributie** instelling is geselecteerd op de **algemene** pagina van de wizard.  

6.  Op de **doel van inhoud** pagina, klikt u op **toevoegen**, kies een van de volgende mogelijkheden van de te voorbereiden distributiepunten en volg de bijbehorende stap:  

    -   **Verzamelingen**: Selecteer **Gebruikersverzamelingen** of **Apparaatverzamelingen**, klik op de verzameling die is gekoppeld aan een of meer distributiepuntengroepen en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  Alleen de verzamelingen die gekoppeld aan een distributiepuntgroep zijn worden weergegeven.  Zie voor meer informatie [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  

    -   **Distributiepunt**: Selecteer een bestaand distributiepunt en klik vervolgens op **OK**. Distributiepunten die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    -   **Distributiepuntengroep**: Selecteer een bestaande distributiepuntgroep en klik vervolgens op **OK**. Distributiepuntgroepen die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    Wanneer u klaar bent met het toevoegen van doelen van inhoud, klikt u op **volgende**.  

7.  Op de **samenvatting** controleert u de instellingen voor de distributie voordat u doorgaat. Als u wilt de inhoud naar de geselecteerde doelen te distribueren, klikt u op **volgende**.  

8.  De **voortgang** pagina geeft de voortgang van de distributie.  

9. De **bevestiging** pagina weergegeven of de inhoud naar de distributiepunten is toegewezen. Om te bewaken de distributie van inhoud, Zie [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

###  <a name="BKMK_ExportContentFromPrestagedContentFile"></a>Stap 3: De inhoud van het voorbereide inhoudsbestand uitpakken  
 Nadat u het voorbereide inhoudsbestand te maken en de inhoud aan distributiepunten toewijzen, kunt u de inhoudsbestanden naar de Inhoudsbibliotheek op een siteserver of distributiepunt uitpakken. Normaal gesproken u het voorbereide inhoudsbestand hebt gekopieerd naar een draagbaar station, zoals een USB-station, of inhoud medium, zoals een DVD hebt gebrand en is deze beschikbaar op de locatie van de siteserver of distributiepunt dat de inhoud is vereist.  

 Gebruik de volgende procedure de inhoudsbestanden handmatig van het voorbereide inhoudsbestand exporteren met behulp van het opdrachtregelprogramma Extract Content.  

> [!IMPORTANT]  
>  Wanneer u het opdrachtregelprogramma uitpakken van inhoud uitvoert, worden in het hulpprogramma een tijdelijk bestand maakt het voorbereide inhoudsbestand wordt gemaakt. Vervolgens het bestand wordt gekopieerd naar de doelmap en het tijdelijke bestand is verwijderd. U moet voldoende schijfruimte voor dit tijdelijke bestand of het proces is mislukt. Het tijdelijke bestand is gemaakt in de volgende locatie:  
>   
>  -   Het tijdelijke bestand wordt gemaakt in dezelfde map die u als doelmap voor het voorbereide inhoudsbestand opgeeft.  

> [!IMPORTANT]  
>  De gebruiker die het opdrachtregelprogramma voor het uitpakken van inhoud uitvoert moet beschikken over **beheerder** rechten op de computer van waaruit u de vooraf geplaatste inhoud wordt uitgepakt.  

##### <a name="to-extract-the-content-files-from-the-prestaged-content-file"></a>De inhoudsbestanden ophalen uit het voorbereide inhoudsbestand  

1.  Kopieer het voorbereide inhoudsbestand naar de computer van waaruit u wilt ophalen van de inhoud.  

2.  Kopieer het opdrachtregelprogramma Extract Content van &lt; *ConfigMgrInstallationPath*> \bin\\&lt;*platform*> op de computer van waaruit u wilt ophalen van het voorbereide inhoudsbestand.  

3.  Open de opdrachtprompt en navigeer naar de locatie van het voorbereide inhoudsbestand en het hulpprogramma voor uitpakken van inhoud.  

    > [!NOTE]  
    >  U kunt een uitpakken of meer voorbereide inhoudsbestanden op een siteserver, secundaire siteserver of distributiepunt.  

4.  Type **extractcontent/p:**&lt;*PrestagedFileLocation*>**\\**&lt;*PrestagedFileName*> **/S** één bestand importeren.  

     Type **extractcontent/p:**&lt;*PrestagedFileLocation*> **/S** voor het importeren van alle voorbereide bestanden in de opgegeven map.  

     Typ bijvoorbeeld **extractcontent /P:D:\PrestagedFiles\MyPrestagedFile.pkgx /S** waar `D:\PrestagedFiles\` is de PrestagedFileLocation `MyPrestagedFile.pkgx` de voorbereide bestandsnaam en `/S` informeert Configuration Manager om op te halen, alleen de inhoudsbestanden die nieuwer zijn dan wat er op het distributiepunt.  

     Wanneer u het voorbereide inhoudsbestand op een siteserver uitpakt, de inhoudsbestanden worden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens de beschikbaarheid van de inhoud is geregistreerd in de site server-database. Wanneer u het voorbereide inhoudsbestand op een distributiepunt exporteert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt, het distributiepunt verzendt een statusbericht naar de bovenliggende primaire siteserver en vervolgens de beschikbaarheid van de inhoud geregistreerd in de sitedatabase.  

    > [!IMPORTANT]  
    >  In het volgende scenario, moet u de inhoud die u hebt opgehaald uit een voorbereid inhoudsbestand wanneer de inhoud wordt bijgewerkt naar een nieuwe versie bijwerken:  
    >   
    >  1.  U maakt een voorbereid inhoudsbestand voor versie 1 van een pakket.  
    >  2.  U werkt de bronbestanden voor het pakket versie 2.  
    >  3.  U uitpakken het voorbereide inhoudsbestand (versie 1 van het pakket) op een distributiepunt.  
    >   
    > Het Pakketversie 2 naar het distributiepunt niet automatisch wordt verzonden door Configuration Manager. U moet een nieuw voorbereid inhoudsbestand dat de nieuwe bestandsversie bevat maken en vervolgens uitpakken van de inhoud, bijwerken van het distributiepunt voor het distribueren van de bestanden die zijn gewijzigd of alle bestanden in het pakket opnieuw distribueren.  

###  <a name="bkmk_dpsiteserver"></a>Het voorbereiden van inhoud op een distributiepunt op een siteserver  
 Wanneer een distributiepunt op een siteserver is geïnstalleerd, moet u de volgende procedure om inhoud met succes voor te bereiden. Dit is omdat de inhoudsbestanden al in de Inhoudsbibliotheek.  

 Wanneer het distributiepunt niet is ingeschakeld voor voorbereide inhoud of wanneer het distributiepunt bevindt zich niet op een siteserver bevindt, ziet de [vooraf geplaatste inhoud gebruiken](#bkmk_prestage) in dit onderwerp.  

##### <a name="to-prestage-content-on-distribution-points-located-on-a-site-server"></a>Voorbereiden van inhoud op distributiepunten die zich bevinden op een siteserver  

1.  Gebruik de volgende stappen uit om te controleren of het distributiepunt niet is ingeschakeld voor voorbereide inhoud.  

    1.  Klik op **Beheer**in de Configuration Manager-console.  

    2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt dat zich op de siteserver bevindt.  

    3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

    4.  Op de **algemene** tabblad, Controleer de **dit distributiepunt inschakelen voor voorbereide inhoud** selectievakje niet is ingeschakeld.  

2.  Het voorbereide inhoudsbestand te maken met behulp van de [stap 1: Een voorbereid inhoudsbestand maken](#BKMK_CreatePrestagedContentFile) in dit onderwerp.  

3.  De inhoud toewijzen aan het distributiepunt met behulp van de [stap 2: De inhoud toewijzen aan distributiepunten](#BKMK_AssignContentToDistributionPoint) in dit onderwerp.  

4.  Op de siteserver, moet u de inhoud van het voorbereide inhoudsbestand uitpakken met behulp van de [stap 3: De inhoud van het voorbereide inhoudsbestand uitpakken](#BKMK_ExportContentFromPrestagedContentFile) in dit onderwerp.  

    > [!NOTE]  
    >  Wanneer het distributiepunt op een secundaire site is, wacht u minstens 10 minuten en vervolgens met behulp van een Configuration Manager-console die is verbonden met de bovenliggende primaire site, de inhoud toewijzen aan het distributiepunt op de secundaire site.  

##  <a name="bkmk_manage"></a>Beheren van de inhoud die u hebt gedistribueerd  
 U hebt de volgende opties voor het beheren van inhoud:  
 - [Inhoud bijwerken](#update-content)
 - [Inhoud opnieuw distribueren](#redistribute-content)
 - [Inhoud verwijderen](#remove-content)
 - [inhoud valideren](#validate-content)

### <a name="update-content"></a>Inhoud bijwerken
Wanneer de locatie van het bronbestand voor een implementatie wordt bijgewerkt door het toevoegen van nieuwe bestanden of bestaande bestanden te vervangen met een nieuwere versie, kunt u de inhoudsbestanden op distributiepunten bijwerken met behulp van de **distributiepunten bijwerken** of **inhoud bijwerken** actie:  
-   De inhoudsbestanden van het bronbestandspad gekopieerd naar de Inhoudsbibliotheek op de site die de pakketinhoudsbron bezit  
-   De pakketversie wordt stapsgewijs verhoogd  
-   Elk exemplaar van de Inhoudsbibliotheek op siteservers en op distributiepunten verwijst updates met alleen de bestanden die zijn gewijzigd  

> [!WARNING]  
>  De pakketversie voor toepassingen is altijd 1. Wanneer u de inhoud voor een toepassingsimplementatietype bijwerkt, maakt Configuration Manager een nieuwe inhouds-ID voor het implementatietype en verwijst het pakket naar de nieuwe inhouds-ID.  

#### <a name="to-update-content-on-distribution-points"></a>Inhoud op distributiepunten bijwerken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassingen die u wilt distribueren. Klik op de **implementatietypen** tabblad en selecteer vervolgens het implementatietype dat u wilt bijwerken.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens de pakketten die u wilt bijwerken.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u wilt bijwerken.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt bijwerken.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen die u wilt bijwerken.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen** > **installatieprogramma's besturingssystemen**, en selecteer vervolgens de installatieprogramma's voor besturingssystemen die u wilt bijwerken.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopieën die u wilt bijwerken.  

3.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**, en klik vervolgens op **OK** om te bevestigen dat u wilt de inhoud bijwerken.  

    > [!NOTE]  
    >  Inhoud voor toepassingen wilt bijwerken, klikt u op de **implementatietypen** tabblad, met de rechtermuisknop op het implementatietype, klik op **inhoud bijwerken**, en klik vervolgens op **OK** om te bevestigen dat u wilt vernieuwen van de inhoud.  

    > [!NOTE]  
    >  Wanneer u inhoud voor opstartinstallatiekopieën bijwerkt, wordt de Wizard distributiepunten beheren geopend. Lees de informatie op de **samenvatting** pagina en voltooi de wizard voor het bijwerken van de inhoud.  

### <a name="redistribute-content"></a>Inhoud opnieuw distribueren
U kunt een pakket alle wilt kopiëren van de inhoudsbestanden in het pakket naar distributiepunten opnieuw distribueren of distributie, wijst u groepen en waardoor de bestaande bestanden overschrijven.  

 Deze bewerking gebruiken om inhoudsbestanden in het pakket herstellen of inhoud opnieuw te verzenden wanneer de initiële distributie mislukt. U kunt een pakket vanuit opnieuw distribueren:  

-   Eigenschappen van pakket  
-   Eigenschappen van het distributiepunt  
-   Eigenschappen van distributiepuntgroepen.  


#### <a name="to-redistribute-content-from-package-properties"></a>Inhoud van de eigenschappen van pakket opnieuw distribueren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** >  **toepassingen**, en selecteer vervolgens de toepassing die u wilt distribueren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt distribueren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** >  **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt distribueren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt distribueren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie van het besturingssysteem die u wilt distribueren.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen** > **installatieprogramma's besturingssystemen**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt distribueren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopie die u wilt distribueren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waarin u wilt distribueren van inhoud, klik op **distribueren**, en klik vervolgens op **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-properties"></a>Inhoud van de eigenschappen van het distributiepunt opnieuw distribueren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarin u inhoud wilt distribueren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud opnieuw wilt distribueren, klik op **distribueren**, en klik vervolgens op **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-group-properties"></a>Inhoud van de eigenschappen van de distributiepuntengroep opnieuw distribueren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **Distributiepuntengroepen**, en selecteer vervolgens de distributiepuntgroep waarin u inhoud wilt distribueren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud opnieuw wilt distribueren, klik op **distribueren**, en klik vervolgens op **OK**.  

    > [!IMPORTANT]  
    >  De inhoud van het pakket wordt gedistribueerd naar alle distributiepunten in de distributiepuntengroep.  


#### <a name="use-the-sdk-to-force-replication-of-content"></a>De SDK gebruiken voor het afdwingen van replicatie van inhoud
U kunt de **RetryContentReplication** klassenmethode Windows Management Instrumentation (WMI) uit de Configuration Manager-SDK om af te dwingen Distribution Manager om inhoud te kopiëren van de bronlocatie naar de Inhoudsbibliotheek.  

Deze methode alleen gebruiken voor het afdwingen van replicatie wanneer u inhoud opnieuw distribueren moet nadat er problemen met normale replicatie van de inhoud zijn (meestal bevestigd door het gebruik van het knooppunt controle van de console).   

Zie voor meer informatie over deze optie SDK [RetryContentReplication methode in klasse SMS_CM_UpdatePackages](https://msdn.microsoft.com/library/mt762092(CMSDK.16).aspx) op MSDN. Microsoft.com.

### <a name="remove-content"></a>Inhoud verwijderen
Wanneer u inhoud niet langer op uw distributiepunten vereist, kunt u de inhoudsbestanden op het distributiepunt.  

-   Eigenschappen van pakket  
-   Eigenschappen van het distributiepunt  
-   Eigenschappen van distributiepuntgroepen.  

Wanneer de inhoud gekoppeld aan een ander pakket dat naar hetzelfde distributiepunt is gedistribueerd is, niet kunt u de inhoud verwijderen.  

#### <a name="to-remove-package-content-files-from-distribution-points"></a>Inhoudsbestanden van pakket verwijderen uit distributiepunten  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt verwijderen:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassing die u wilt verwijderen.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt verwijderen.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt verwijderen.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt verwijderen.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie van het besturingssysteem die u wilt verwijderen.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen** > **installatieprogramma's besturingssystemen**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt verwijderen.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** > **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopie die u wilt verwijderen.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waaruit u wilt verwijderen van de inhoud, klikt u op **verwijderen**, en klik vervolgens op **OK**.  

#### <a name="to-remove-package-content-from-distribution-point-properties"></a>Pakketinhoud verwijderen uit de eigenschappen van distributiepunt  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarop u wilt verwijderen van de inhoud.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud wilt verwijderen, klikt u op **verwijderen**, en klik vervolgens op **OK**.  

#### <a name="to-remove-content-from-distribution-point-group-properties"></a>Inhoud uit eigenschappen van distributiepuntgroepen te verwijderen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **Distributiepuntengroepen**, en selecteer vervolgens de distributiepuntgroep waarin u inhoud wilt verwijderen.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud wilt verwijderen, klikt u op **verwijderen**, en klik vervolgens op **OK**.  


### <a name="validate-content"></a>Inhoud valideren
Het inhoudsvalidatieproces controleert de integriteit van inhoudsbestanden op distributiepunten. U inhoudsvalidatie op basis van een planning inschakelt of u kunt de validatie van de inhoud van de eigenschappen van distributiepunten en pakketten handmatig starten.  

 Wanneer de inhoudsvalidatie start, Configuration Manager controleert of de inhoudsbestanden op distributiepunten en als de bestandshash niet verwacht voor de bestanden op het distributiepunt wordt, Configuration Manager een statusbericht dat u kunt bekijken gemaakt in de **bewaking** werkruimte.  

 Zie voor meer informatie over het configureren van de planning voor inhoudsvalidatie [configuraties van het distributiepunt](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  


#### <a name="to-initiate-content-validation-for-all-content-on-a-distribution-point"></a>Validatie van inhoud voor alle inhoud op een distributiepunt starten  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarin u inhoud wilt valideren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Op de **inhoud** tabblad, selecteert u het pakket waarin u wilt valideren van de inhoud, klikt u op **valideren**, klikt u op **OK**, en klik vervolgens op **OK**. Het inhoudsvalidatieproces wordt geïnitieerd voor het pakket op het distributiepunt.  

5.  De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en klik op de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven. Zie voor meer informatie over het controleren van inhoudstatussen [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

#### <a name="to-initiate-content-validation-for-a-package"></a>Validatie van inhoud voor een pakket initiëren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt valideren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassing die u wilt valideren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt valideren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt valideren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt valideren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie van het besturingssysteem die u wilt valideren.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen** >  **installatieprogramma's besturingssystemen**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt valideren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** > **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopie die u wilt voorbereiden.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waarin u de inhoud, klikt u op valideren **valideren**, klikt u op **OK**, en klik vervolgens op **OK**. Het inhoudvalidatieproces wordt gestart voor de inhoud op het geselecteerde distributiepunt of distributiepuntengroep.  

5.  De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en klik op de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven. Zie voor meer informatie over het controleren van inhoudstatussen [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  
