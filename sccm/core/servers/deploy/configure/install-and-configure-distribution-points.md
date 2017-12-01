---
title: Distributiepunten beheren
titleSuffix: Configuration Manager
description: De inhoud (bestanden en software) die u op apparaten en gebruikers implementeert met distributiepunten hosten. Hier wordt het installeren en configureren.
ms.custom: na
ms.date: 09/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: "5"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b1b0183bcd2550ca5444eba417e70129be1b92bb
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>Installeren en configureren van distributiepunten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager-distributiepunten voor het hosten van de inhoud die u op apparaten en gebruikers implementeert (bestanden en software) installeren. U kunt ook distributie punt groepen maken die hoe u distributiepunten wilt beheren en hoe u inhoud naar distributiepunten distribueren vereenvoudigen.  

 Wanneer u *een nieuw distributiepunt installeert* (via de installatiewizard) of *beheren van de eigenschappen van een bestaand distributiepunt* (het distributiepunt door eigenschappen te bewerken), kunt u de meeste van de distributiepuntinstellingen configureren. Enkele instellingen zijn alleen beschikbaar wanneer u bent u installeert of bewerkt, maar niet beide:  

-   De instellingen die beschikbaar zijn alleen wanneer u een distributiepunt installeert:  

    -   **Configuration Manager IIS te installeren op de distributiepuntcomputer toestaan**

    -   **De schijfruimte-instellingen voor het distributiepunt configureren**  

-   De instellingen die beschikbaar zijn alleen wanneer u de eigenschappen van een distributiepunt bewerkt:  

    -   **Relaties tussen distributiepunten beheren**  

    -   **Inhoud weergeven geïmplementeerd op het distributiepunt.**  

    -   **Snelheidslimieten configureren voor de gegevensoverdracht naar distributiepunten**  

    -   **Schema's configureren voor de gegevensoverdracht naar distributiepunten**  

##  <a name="bkmk_install"></a>Een distributiepunt installeren  
U moet een sitesysteemserver toewijzen als een distributiepunt voordat inhoud kan worden gemaakt voor clientcomputers beschikbaar. U moet ook een distributiepunt toewijzen aan ten minste één [grensgroep](/sccm/core/servers/deploy/configure/boundary-groups#distribution-points) voordat lokale clientcomputers dat distributiepunt als bronlocatie voor inhoud kunnen gebruiken. U kunt de siterol van distributiepunt toevoegen aan een nieuwe sitesysteemserver of de siterol toevoegen aan een bestaande sitesysteemserver.


 Wanneer u een nieuw distributiepunt installeert, gebruikt u een installatiewizard die u bij de beschikbare instellingen helpt. Voordat u begint, moet u rekening houden met het volgende:  

-   U moet de volgende beveiligingsmachtigingen hebben om te maken en configureren van een distributiepunt:  

    -   **Lees** voor de **distributiepunt** object  

    -   **Kopiëren naar distributiepunt** voor de **distributiepunt** object  

    -   **Wijzig** voor de **Site** object  

    -   **Certificaten beheren voor implementatie van besturingssysteem** voor de **Site** object  

-   Internet Information Services (IIS) moet worden geïnstalleerd op de server die als voor het distributiepunt host fungeert. Wanneer u de sitesysteemrol installeert, wordt dit door Configuration Manager kunt installeren en configureren van IIS voor u.  

Gebruik de volgende algemene procedures om te installeren of een distributiepunt te wijzigen. Zie voor meer informatie over de beschikbare configuratieopties, de [een distributiepunt configureren](#bkmk_configs) sectie van dit onderwerp.  

#### <a name="to-install-a-distribution-point"></a>Om een distributiepunt te installeren  

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Servers en sitesysteemrollen**.  

2.  De sitesysteemrol distributiepunt toevoegen aan een nieuwe of bestaande sitesysteemserver:  

    -   **Nieuwe sitesysteemserver**: Op de **Start** tabblad, in de **maken** groep, kiest u **Sitesysteemserver maken**. De wizard Sitesysteemserver maken wordt geopend.  

    -   **Bestaande sitesysteemserver**: Kies de server waarin u wilt installeren van de sitesysteemrol distributiepunt. Wanneer u een server kiezen, wordt een lijst met de sitesysteemrollen die al zijn geïnstalleerd op de server wordt weergegeven in het deelvenster met resultaten.  

         Op de **Start** tabblad, in de **Server** groep, kiest u **Sitesysteemrol toevoegen**. Hiermee opent u de wizard Sitesysteemrollen toevoegen.  

3.  Op de pagina **Algemeen** specificeert u de algemene instellingen voor de sitesysteemserver. Wanneer u het distributiepunt aan een bestaande sitesysteemserver toevoegt, controleert u of de waarden die eerder zijn geconfigureerd.  

4.  Op de **Systeemrolselectie** pagina **distributiepunt** uit de lijst met beschikbare rollen en kies vervolgens **volgende**.  

5.  Zie voor de volgende pagina's van de wizard de informatie in de [een distributiepunt configureren](#bkmk_configs) sectie.  

     Bijvoorbeeld, als u naar het distributiepunt als een pull-distributiepunt installeert, kiest u **Schakel dit distributiepunt voor het ophalen van inhoud van andere distributiepunten** en breng vervolgens de aanvullende configuraties die pull-distributiepunten vereisen.  

6.  Nadat u de wizard hebt voltooid, wordt de siterol van distributiepunt toegevoegd aan de sitesysteemserver.  

#### <a name="to-change-a-distribution-point"></a>Een distributiepunt wijzigen  

1.  Kies in de Configuration Manager-console **beheer** >  **distributiepunten**, en selecteer vervolgens het distributiepunt dat u wilt configureren.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

3.  Gebruik de informatie in de [een distributiepunt configureren](#bkmk_configs) sectie wanneer u de eigenschappen van het distributiepunt bewerkt.  

4.  Nadat u de gewenste wijzigingen hebt aangebracht, uw instellingen opslaan en sluiten van de eigenschappen van het distributiepunt.  

##  <a name="bkmk_manage"></a>Distributiepuntgroepen beheren  
 Distributiepuntgroepen bieden een logische groepering van distributiepunten voor inhoudsdistributie. U kunt deze groepen gebruiken om te beheren en controleren van inhoud vanaf een centrale locatie voor distributiepunten die meerdere sites omvatten. Houd rekening met het volgende:

-   U kunt een of meer distributiepunten van elke site in de hiërarchie toevoegen aan een distributiepuntgroep.  

-   U kunt een distributiepunt toevoegen aan meer dan één distributiepuntgroep.  

-   Wanneer u inhoud naar een distributiepuntgroep distribueert, distribueert Configuration Manager de inhoud naar alle distributiepunten die lid van de distributiepuntgroep zijn.  

-   Als u een distributiepunt aan de distributiepuntgroep na een initiële inhoudsdistributie toevoegt, distribueert Configuration Manager automatisch de inhoud naar het nieuwe distributiepuntlid.  

-   U kunt een verzameling koppelen aan een distributiepuntgroep. Wanneer u inhoud naar die verzameling distribueert, bepaalt Configuration Manager welke distributiepuntengroepen zijn gekoppeld aan de verzameling. De inhoud wordt dan gedistribueerd naar alle distributiepunten die lid van deze distributiepuntgroepen zijn.  

    > [!NOTE]  
    >  Nadat u inhoud naar een verzameling, distribueert de verzameling daarna hebt gekoppeld aan een nieuwe distributiepuntgroep, moet u de inhoud aan de verzameling opnieuw distribueren voordat de inhoud wordt gedistribueerd naar de nieuwe distributiepuntgroep.  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>Maken en configureren van een nieuwe distributiepuntgroep  

1.  Kies in de Configuration Manager-console **beheer** > **Distributiepuntengroepen**.  

2.  Op de **Start** tabblad, in de **maken** groep, kiest u **groep maken**.  

3.  Voer de naam en beschrijving voor de distributiepuntengroep.  

4.  Op de **verzamelingen** Kies **toevoegen**, selecteer de verzamelingen die u wilt koppelen aan de distributiepuntengroep en kies vervolgens **OK**.  

5.  Op de **leden** Kies **toevoegen**, selecteer de distributiepunten die u wilt toevoegen als leden van de distributiepuntengroep en kies vervolgens **OK**.  

6.  Kies **OK** voor het maken van de distributiepuntgroep.  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>Distributiepunten toevoegen en verzamelingen koppelen aan een bestaande distributiepuntengroep  

1.  Kies in de Configuration Manager-console **beheer** > **Distributiepuntengroepen**.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

3.  Op de **verzamelingen** Kies **toevoegen** selecteren de verzamelingen die u wilt koppelen aan de distributiepuntengroep en kies vervolgens **OK**.  

4.  Op de **leden** Kies **toevoegen** selecteren van de distributiepunten die u wilt toevoegen als leden van de distributiepuntengroep en kies vervolgens **OK**.  

5.  Kies **OK** wijzigingen aan de distributiepuntgroep wilt opslaan.  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>Geselecteerde distributiepunten toevoegen verwijst naar een nieuwe distributiepuntgroep  

1.  Kies in de Configuration Manager-console **beheer** > **distributiepunten**, en selecteer vervolgens de distributiepunten die u wilt toevoegen aan de nieuwe distributiepuntgroep.  

2.  Op de **Start** tabblad, in de **distributiepunt** groep uit, vouw **geselecteerde Items toevoegen**, en kies vervolgens **geselecteerde Items toevoegen aan nieuwe Distributiepuntengroepen**.  

3.  Voer de naam en beschrijving voor de distributiepuntengroep.  

4.  Op de **verzamelingen** Kies **toevoegen** selecteren de verzamelingen die u wilt koppelen aan de distributiepuntengroep en kies vervolgens **OK**.  

5.  Op de **leden** tabblad, controleert u of dat u wilt dat de vermelde distributiepunten toevoegen als leden van de distributiepuntgroep in Configuration Manager. Kies **toevoegen** de distributiepunten toevoegen en klik vervolgens op **OK**.  

6.  Kies **OK** voor het maken van de distributiepuntgroep.  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>Verwijst naar geselecteerde distributiepunten toevoegen aan bestaande distributiepuntgroepen  

1.  Kies in de Configuration Manager-console **beheer** > **distributiepunten**, en selecteer vervolgens de distributiepunten die u wilt toevoegen aan de nieuwe distributiepuntgroep.  

2.  Op de **Start** tabblad, in de **distributiepunt** groep uit, vouw **geselecteerde Items toevoegen**, en kies vervolgens **geselecteerde Items toevoegen aan bestaande Distributiepuntgroepen**.  

3.  In de **beschikbare distributiepuntengroepen**, selecteer de distributiepuntgroepen waaraan de geselecteerde distributiepunten als leden worden toegevoegd en kies vervolgens **OK**.  

##  <a name="bkmk_configs"></a>Een distributiepunt configureren  
 Individuele distributiepunten bieden ondersteuning voor een groot aantal verschillende configuraties. Niet alle typen distributiepunten worden echter alle configuraties ondersteund. Cloud-gebaseerde distributiepunten ondersteunen bijvoorbeeld geen inhoudsimplementaties die zijn ingeschakeld voor PXE of multicast. In de volgende onderwerpen vindt u informatie over specifieke beperkingen:  

-   [Een cloud-gebaseerd distributiepunt gebruiken met System Center Configuration Manager](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [Een pull-distributiepunt met System Center Configuration Manager gebruiken](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

De volgende secties worden de configuraties die u selecteren kunt wanneer u een nieuw distributiepunt installeert of de eigenschappen van een bestaand distributiepunt bewerkt.  

### <a name="general"></a>Algemeen  
 De algemene distributiepuntinstellingen configureren:  

-   **Installeer en Configureer IIS indien vereist door Configuration Manager**: Kies deze instelling om Configuration Manager installeren en configureren van IIS op de server als deze nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten. Als IIS is niet geïnstalleerd op de server en u deze instelling niet selecteert, moet u IIS installeren voordat het distributiepunt kan worden geïnstalleerd.  

    > [!NOTE]  
    >  Deze optie is beschikbaar, alleen wanneer u een nieuw distributiepunt installeert.  

- **BranchCache inschakelen en configureren voor dit distributiepunt**: Kies deze instelling om Configuration Manager Windows BranchCache configureren op de distributiepuntserver. Zie voor meer informatie over het gebruik van Windows BranchCache met System Center Configuration Manager [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache) in *ondersteuning voor Windows-onderdelen en -netwerken in System Center Configuration Manager*.

-   **Configureren hoe clientapparaten communiceren met het distributiepunt**: Er zijn voor- en nadelen via HTTP en HTTPS. Zie voor meer informatie 'Aanbevolen beveiligingsprocedures voor inhoudsbeheer' in [basisconcepten voor inhoudsbeheer in System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   **Clients toestaan anoniem verbinding te**: Deze instelling bepaalt u of het distributiepunt anonieme verbindingen van Configuration Manager-clients naar de Inhoudsbibliotheek toestaat.  

    > [!IMPORTANT]  
    >  Reparatie van een Windows Installer-toepassing kan mislukken voor een client wanneer u deze instelling niet gebruikt.  
    >   
    >  Wanneer u een Windows Installer-toepassing op een Configuration Manager-client implementeert, wordt in Configuration Manager het bestand naar de lokale cache op de client gedownload. De bestanden eventueel verwijderd nadat de installatie is voltooid.
    >  
    >  Configuration Manager-client werkt de bronlijst voor Windows Installer voor de geïnstalleerde Windows Installer-toepassingen met het Inhoudspad voor de Inhoudsbibliotheek op gekoppelde distributiepunten. Later, als u de herstelactie van programma verwijderen of op een Configuration Manager-client start, probeert MSIExec toegang tot het Inhoudspad met een anonieme gebruiker.  
    >   
    >  U kunt echter de updates beschreven in de Microsoft Knowledge Base-artikel installeren [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) en wijzigt u vervolgens een registersleutel om dit gedrag te wijzigen.  
    >   
    >  Nadat de update is geïnstalleerd op de clients, heeft MSIExec toegang tot het Inhoudspad met behulp van het aangemelde gebruikersaccount wanneer u geen kiest de **clients toestaan anoniem verbinding te** instelling.  

-   **Een zelfondertekend certificaat maken of importeren van een clientcertificaat voor openbare-sleutelinfrastructuur (PKI) voor het distributiepunt**: Het certificaat heeft de volgende doeleinden:  

    -   Hiermee verifieert het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

    -   Als u controleert de **PXE-ondersteuning inschakelen voor clients** vak op de **PXE-instellingen** pagina, wordt het certificaat verzonden naar computers die een PXE-opstartbewerking uitvoeren, zodat ze verbinding met een beheerpunt tijdens de implementatie van het besturingssysteem maken kunnen.  

    Wanneer uw beheerpunten in de site zijn geconfigureerd voor HTTP, maakt u een zelfondertekend certificaat. Wanneer uw beheerpunten zijn geconfigureerd voor HTTPS, moet u een PKI-clientcertificaat importeren.  

    Blader naar een Public Key Cryptography Standard (PKCS #12) dat een PKI-certificaat met de volgende vereisten voor Configuration Manager heeft voor het importeren van het certificaat:  

    -   Bedoelde gebruik moet clientverificatie omvatten.  

    -   De persoonlijke sleutel moet exporteerbaar zijn ingeschakeld.  

    > [!TIP]  
    >  Er zijn geen specifieke vereisten voor het certificaatonderwerp of alternatieve onderwerpnaam (SAN) en u kunt hetzelfde certificaat gebruiken voor meerdere distributiepunten.  

     Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) voor meer informatie over de certificaatvereisten.  

     Voor een Voorbeeldimplementatie van dit certificaat, Zie de sectie 'Implementeren van de Client-certificaat voor distributiepunten' in [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

-   **Dit distributiepunt inschakelen voor voorbereide inhoud**: Kies deze instelling naar het distributiepunt inschakelen voor voorbereide inhoud. Wanneer deze instelling is geselecteerd, kunt u distributiegedrag configureren wanneer u inhoud distribueert. U kunt kiezen om altijd een van de volgende:

 - De inhoud op het distributiepunt voor te bereiden.
 - De initiële inhoud voor het pakket voor te bereiden, maar het normale inhouddistributieproces gebruiken wanneer er updates voor de inhoud.
 - Het normale inhouddistributieproces gebruiken voor de inhoud van het pakket.  

### <a name="drive-settings"></a>Stationsinstellingen  

> [!NOTE]  
>  Deze opties zijn alleen beschikbaar wanneer u een nieuw distributiepunt installeert.  

Geef de Stationsinstellingen voor het distributiepunt. U kunt maximaal twee schijfstations voor de Inhoudsbibliotheek en twee schijfstations voor de pakketshare configureren. Configuration Manager kan extra stations kan gebruiken wanneer de eerste twee de geconfigureerde stationsruimtereserve bereiken. De **Stationsinstellingen** pagina configureert de prioriteit voor de schijfstations en de hoeveelheid vrije schijfruimte die overblijft op elk schijfstation.  

-   **Gereserveerde ruimte op station (MB)**: De waarde die u voor deze instelling configureert bepaalt de hoeveelheid vrije ruimte op een station voordat Configuration Manager een ander station kiest en verdergaat met het kopieerproces naar dat station. Inhoudsbestanden kunnen meerdere stations omvatten.  

-   **Inhoudslocaties**: Geef de inhoudslocaties op voor de inhoud en de pakketshare. Configuration Manager kopieert inhoud naar de primaire Inhoudslocatie, totdat de hoeveelheid vrije ruimte heeft bereikt voor de opgegeven waarde voor **vrije schijfruimte (MB) reserveren**. De inhoudslocaties zijn standaard ingesteld op **automatische**. De primaire Inhoudslocatie is ingesteld op het schijfstation dat de meeste schijfruimte bij de installatie heeft en de secundaire locatie wordt toegewezen aan het schijfstation dat de tweede meeste vrije schijfruimte heeft. Wanneer de primaire en secundaire stations de gereserveerde ruimte op station bereiken, wordt Configuration Manager selecteert een ander beschikbaar station met de meeste vrije schijfruimte en blijft het kopieerproces.  

> [!NOTE]  
>  Om te voorkomen dat Configuration Manager op een specifiek station wordt geïnstalleerd, maakt u een leeg bestand met de naam **no_sms_on_drive.sms** en kopieer het naar de hoofdmap van het station voordat u het distributiepunt installeert.  

### <a name="pull-distribution-point"></a>Pull-distributiepunt  
Wanneer u de optie **Schakel dit distributiepunt voor het ophalen van inhoud van andere distributiepunten**, u het gedrag van de manier waarop die computer, wordt de inhoud die u naar het distributiepunt distribueert wijzigen. Een pull-distributiepunt wordt.  

Voor elk pull-distributiepunt dat u configureert, moet u een of meer brondistributiepunten van waaruit het pull-distributiepunt, de inhoud wordt opgeven:  

-   Kies **toevoegen**, en selecteer vervolgens een of meer van de beschikbare distributiepunten als brondistributiepunten.  

-   Kies **verwijderen** verwijderen van het geselecteerde distributiepunt als een brondistributiepunt.  

-   Gebruik de pijltjesknoppen om aan te passen, de volgorde waarin het pull-distributiepunt contactpersonen die de bron distributiepunten wanneer het pull-distributiepunt probeert om inhoud te brengen. Distributiepunten met de laagste waarde worden eerst bereikt.  

### <a name="pxe"></a>PXE  
Geef op of PXE moet worden ingeschakeld op het distributiepunt. Wanneer u PXE inschakelt, installeert Configuration Manager Windows Deployment Services op de server, indien nodig. Windows Deployment Services is de service die de PXE-opstart om besturingssystemen te installeren uitvoert. Nadat u de wizard om het distributiepunt te maken, installeert Configuration Manager een provider in Windows Deployment Services die de PXE-opstartfuncties gebruikt.  

Wanneer u de optie **PXE-ondersteuning inschakelen voor clients**, configureer de volgende instellingen:  

-   **Dit distributiepunt reageert op binnenkomende PXE-aanvragen toestaan**: Geef op of Windows Deployment Services inschakelen zodat het reageert op PXE-serviceaanvragen. Gebruik dit vak inschakelen en uitschakelen van de service zonder dat de PXE-functionaliteit verwijderd uit het distributiepunt.  

-   **Schakel onbekende computerondersteuning**: Geef op of ondersteuning voor computers die Configuration Manager niet beheert inschakelen.  

-   **Een wachtwoord verplicht stellen wanneer computers PXE gebruiken**: Geef een sterk wachtwoord voor extra beveiliging voor uw PXE-implementaties.  

-   **Affiniteit van gebruikersapparaat**: Geef op hoe het distributiepunt gebruikers moet koppelen aan de doelcomputer voor PXE-implementaties. Kies een van de volgende opties:  

    -   **Gebruikersaffiniteit apparaat met automatische goedkeuring toestaan**: Kies deze instelling om gebruikers automatisch koppelen aan de doelcomputer zonder te wachten op goedkeuring.  

    -   **Affiniteit van gebruikersapparaat in afwachting van goedkeuring door beheerder toestaan**: Kies deze instelling moet worden gewacht op goedkeuring van een gebruiker met beheerdersrechten voordat gebruikers aan de doelcomputer gekoppeld worden.  

    -   **Geen affiniteit tussen gebruikers en apparaten toestaan**: Kies deze instelling om op te geven dat gebruikers niet gekoppeld aan de doelcomputer zijn.  

     Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md) voor meer informatie over de gebruikersaffiniteit van het apparaat.  

-   **Netwerkinterfaces**: Geef op dat het distributiepunt reageert op PXE-aanvragen van alle netwerkinterfaces of van specifieke netwerkinterfaces. Als het distributiepunt op specifieke netwerkinterfaces reageert, moet u het MAC-adres voor elke netwerkinterface opgeven.  

-   **Geef de Reactievertraging van de PXE-server (seconden)**: Geef in seconden op hoe lang de vertraging is voordat het distributiepunt reageert op computeraanvragen wanneer er meerdere distributiepunten met PXE-functionaliteit worden gebruikt. Standaard de Configuration Manager PXE-servicepunt antwoordt eerst PXE-aanvragen van het netwerk.  

> [!NOTE]  
>  Het PXE-protocol kunt u implementaties van besturingssystemen aan Configuration Manager-clientcomputers starten. Configuration Manager gebruikt de siterol distributiepunt met PXE-functionaliteit voor het initiëren van het implementatieproces van het besturingssysteem. Het distributiepunt met PXE-functionaliteit moet worden geconfigureerd voor:
>
> 1. Reageren op PXE-opstartaanvragen die Configuration Manager-clients op het netwerk.
> 2. Met de Configuration Manager-infrastructuur om te bepalen welke implementatieacties te laten werken.  

### <a name="multicast"></a>Multicast  
Geef op of multicast op het distributiepunt moet worden ingeschakeld. Wanneer u multicast inschakelt, installeert Configuration Manager Windows Deployment Services op de server, indien nodig.  

Als u controleert de **multicast inschakelen om gelijktijdig gegevens verzenden naar meerdere clients** Configureer de volgende instellingen:  

-   **Multicastverbindingsaccount**: Geef de account moet worden gebruikt wanneer u Configuration Manager-databaseverbindingen voor multicast configureert.  

-   **Multicastadresinstellingen**: Geef het IP-adressen voor het verzenden van gegevens naar de doelcomputers. Standaard wordt het IP-adres verkregen van een DHCP-server die is ingeschakeld voor het distribueren van multicastadressen. Afhankelijk van de netwerkomgeving, kunt u een bereik met IP-adressen van 239.0.0.0 tot en met 239.255.255.255.  

    > [!IMPORTANT]  
    >  De IP-adressen die u configureert moet toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Controleer of routers en firewalls toestaan voor multicast-verkeer tussen de doelcomputer en de siteserver.  

-   **UDP-poortbereik voor multicast**: Geef het bereik van User Datagram Protocol (UDP)-poorten die worden gebruikt om gegevens te verzenden naar de doelcomputers.  

    > [!IMPORTANT]  
    >  De UDP-poorten moeten toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Controleer of routers en firewalls toestaan voor multicast-verkeer tussen de doelcomputer en de siteserver.  

-   **Overdrachtssnelheid van client**: Selecteer de overdrachtssnelheid die wordt gebruikt om gegevens te downloaden naar de doelcomputers.  

-   **Maximum aantal clients**: Geef het maximum aantal doelcomputers op dat het besturingssysteem vanaf dit distributiepunt kan downloaden.  

-   **Geplande multicast inschakelen**: Geef op hoe Configuration Manager bepaalt wanneer kan ik besturingssystemen implementeren op doelcomputers. Configureer de volgende opties:  

    -   **Startvertraging van sessie (minuten)**: Geef het aantal minuten dat Configuration Manager wacht voordat het reageert op de eerste implementatieaanvraag.  

    -   **Minimale sessiegrootte (clients)**: Geef op hoeveel aanvragen er moeten worden ontvangen voordat Configuration Manager begint met de implementatie van het besturingssysteem.  

> [!NOTE]  
>  Multicastimplementaties houden netwerkbandbreedte vrij door gegevens gelijktijdig te verzenden naar meerdere Configuration Manager-clients in plaats van een kopie van de gegevens verzenden naar elke client via een aparte verbinding. Zie voor meer informatie over het gebruik van multicast voor de implementatie van besturingssystemen, [multicast gebruiken om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

### <a name="group-relationships"></a>Groepsrelaties  

> [!NOTE]  
>  Deze opties zijn alleen beschikbaar wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

Beheer de distributiepuntengroepen die dit distributiepunt lid is.  

Kies voor dit distributiepunt als een lid toevoegen aan een bestaande distributiepuntgroep, **toevoegen**. Selecteer een bestaande distributiepuntgroep in de lijst in de **toevoegen aan Distributiepuntgroepen** dialoogvenster vak in en kies vervolgens **OK**.  

Als dit distributiepunt uit een distributiepuntgroep wilt verwijderen, selecteert u de distributiepuntgroep in de lijst en kies vervolgens **verwijderen**.  

### <a name="content"></a>Inhoud  

> [!NOTE]  
>  Deze opties zijn alleen beschikbaar wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

Beheren van de inhoud die naar het distributiepunt is gedistribueerd. De **implementatiepakketten** sectie geeft een lijst van de pakketten die gedistribueerd naar dit distributiepunt. U kunt een pakket in de lijst selecteren en de volgende acties uitvoeren:  

-   **Valideren**: Start het proces voor het valideren van de integriteit van de inhoudsbestanden in het pakket. De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en kies vervolgens de **inhoudsstatus** knooppunt.  

-   **Opnieuw distribueren**: Kopieert alle inhoudsbestanden in het pakket naar het distributiepunt en worden de bestaande bestanden overschreven. Deze actie wordt meestal gebruikt voor het repareren van inhoudsbestanden in het pakket.  

-   **Verwijder**: Hiermee verwijdert u de inhoudsbestanden van het distributiepunt voor het pakket.  

### <a name="content-validation"></a>Validatie van inhoud  
Geef op of het instellen van een planning voor het valideren van de integriteit van inhoudsbestanden op het distributiepunt. Wanneer u inhoudsvalidatie op een planning inschakelt, wordt Configuration Manager begint het proces op het geplande tijdstip en wordt alle inhoud op het distributiepunt gecontroleerd. U kunt ook de prioriteit voor validatie van inhoud configureren. De prioriteit is standaard ingesteld op **laagste**.  

De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en kies vervolgens de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, software-updatepakket en installatiekopie) wordt weergegeven.  

> [!WARNING]  
>  Hoewel u de planning voor inhoudsvalidatie opgeven met behulp van de lokale tijd voor de computer, ziet u de Configuration Manager-console de planning in UTC.  

### <a name="boundary-group"></a>Grensgroep  
Beheer de grensgroepen waaraan dit distributiepunt is toegewezen. Wilt u het distributiepunt toevoegen aan ten minste één grensgroep. Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan een distributiepunt dat distributiepunt als bronlocatie voor inhoud te gebruiken.

Aanvullend:

- Voordat u versie 1610, kunt u controleren de **clients gebruiken dit sitesysteem als een terugvalbronlocatie voor inhoud toestaan** vak wilt toestaan dat clients buiten deze grensgroepen terug te vallen en het distributiepunt gebruiken als bronlocatie voor inhoud, wanneer er geen andere distributiepunten beschikbaar zijn. Zie voor meer informatie over grensgroepen [grensgroepen voor versie 1511, 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606). Zie voor voorkeursdistributiepunten, [basisconcepten voor inhoudsbeheer in System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).

- Versie 1610 of hoger, configureert u grensgroep *relaties* die definiëren wanneer en tot welke grensgroepen een client terugvallen om inhoud te zoeken. Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


### <a name="schedule"></a>Planning  

> [!NOTE]  
>  Deze opties zijn alleen beschikbaar wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

> [!TIP]  
>  Op dit tabblad is alleen beschikbaar wanneer u de eigenschappen bewerkt van een distributiepunt dat zich op afstand van de siteservercomputer.  

 Geef op of configureer een planning die beperkt wanneer Configuration Manager kan de gegevens naar het distributiepunt kan overdragen.  

> [!IMPORTANT]  
>  De planning is gebaseerd op de tijdzone van de verzendende site, niet het distributiepunt.  

Als u wilt gegevens beperken, selecteert u de periode en kies een van de volgende instellingen voor **beschikbaarheid**:  

-   **Open voor alle prioriteiten**: Geeft aan of Configuration Manager gegevens naar het distributiepunt zonder beperkingen verzendt.  

-   **Gemiddelde en hoge prioriteit toestaan**: Hiermee geeft u dat Configuration Manager alleen de gegevens over gemiddelde en hoge prioriteit naar het distributiepunt verzendt.  

-   **Alleen hoge prioriteit toestaan**: Geeft aan of Configuration Manager alleen hoge prioriteit gegevens naar het distributiepunt verzendt.  

-   **Gesloten**: Geeft aan of Configuration Manager niet alle gegevens naar het distributiepunt verzenden.  

U kunt gegevens beperken door de prioriteit of de verbinding gedurende geselecteerde perioden te sluiten.  

### <a name="rate-limits"></a>Frequentielimieten  

> [!NOTE]  
>  Deze opties zijn alleen beschikbaar wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

> [!TIP]  
>  Op dit tabblad is alleen beschikbaar wanneer u de eigenschappen bewerkt van een distributiepunt dat zich op afstand van de siteservercomputer.  

Geef op of voor het configureren van frequentielimieten voor het beheren van de netwerkbandbreedte die wordt gebruikt bij Configuration Manager overdracht van inhoud naar het distributiepunt. U kunt kiezen uit de volgende opties:  

-   **Onbeperkt bij verzenden naar deze bestemming**: Deze optie geeft aan of Configuration Manager inhoud naar het distributiepunt met zonder frequentielimietbeperkingen verzendt.  

-   **Pulsmodus**: Deze optie geeft de grootte van de gegevensblokken die naar het distributiepunt worden verzonden. U kunt daarnaast een vertraging tussen het verzenden van de afzonderlijke gegevensblokken opgeven. Gebruik deze optie wanneer u gegevens via een netwerkverbinding met zeer lage bandbreedte naar het distributiepunt verzendt. U wellicht bijvoorbeeld beperkingen instellen om te verzenden van 1 KB aan gegevens om de vijf seconden, ongeacht de snelheid van de koppeling of het gebruik ervan op een bepaald moment.  

-   **Beperkt tot opgegeven maximale overdrachtssnelheid per uur**: Geef deze instelling om een site gegevens verzenden naar een distributiepunt met behulp van alleen het percentage tijd dat u configureert. Als u deze optie gebruikt, wordt Configuration Manager geeft niet de beschikbare bandbreedte van het netwerk, maar verdeelt het de tijd die het gegevens kan verzenden. Gegevens worden vervolgens verzonden voor een kort tijdsblok, gevolgd door tijdsblokken waarin geen gegevens worden verzonden. Bijvoorbeeld, als de maximale snelheid wordt ingesteld op **50%**, Configuration Manager brengt gegevens over voor een bepaalde tijd, gevolgd door een even lange periode waarin geen gegevens worden verzonden. De werkelijke hoeveelheid gegevens, of grootte van het gegevensblok, wordt hiermee niet beheerd. Alleen de hoeveelheid tijd waarin gegevens worden verzonden, wordt beheerd.  
