---
title: Distributiepunten beheren | Microsoft-documenten
description: De inhoud (bestanden en software) die u implementeert op apparaten en gebruikers met distributiepunten hosten. Hier wordt het installeren en configureren.
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8728d9f2ae63282a8f58b20105e488fb1a5ef55b
ms.openlocfilehash: 4c94e4de5bbfe621492e8682c9424a48eb38196d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>Installeren en configureren van distributiepunten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*
 
U installeert System Center Configuration Manager-distributiepunten als host voor de inhoud (bestanden en software) die u op apparaten en gebruikers implementeert. U kunt ook distributie punt groepen maken die hoe u distributiepunten beheert en hoe u inhoud distribueert naar distributiepunten vereenvoudigen.  

 Wanneer u *installeren van een nieuw distributiepunt* (met behulp van de installatiewizard) of *beheren van de eigenschappen van een bestaand distributiepunt* (het distributiepunt door eigenschappen te bewerken), kunt u de meeste instellingen voor distributiepunten. Een paar instellingen zijn alleen beschikbaar als u wilt installeren of bewerkt, maar niet allebei:  

-   Instellingen die beschikbaar zijn alleen wanneer u een distributiepunt installeert:  

    -   **Configuration Manager IIS te installeren op de distributiepuntcomputer toestaan**

    -   **Station ruimte instellingen configureren voor het distributiepunt.**  

-   Instellingen die beschikbaar zijn alleen wanneer u de eigenschappen van een distributiepunt bewerkt:  

    -   **Distribution point groepsrelaties beheren**  

    -   **De inhoud gedistribueerd naar het distributiepunt**  

    -   **Snelheidslimieten configureren voor gegevensoverdrachten naar distributiepunten**  

    -   **Schema's configureren voor gegevensoverdrachten naar distributiepunten**  

##  <a name="bkmk_install"></a>Een distributiepunt installeert  
 U moet een sitesysteemserver aanduiden als een distributiepunt voordat inhoud beschikbaar is op clientcomputers kan worden gemaakt. U kunt de siterol van distributiepunt toevoegen aan een nieuwe sitesysteemserver of de siterol toevoegen aan een bestaande sitesysteemserver.  

 Wanneer u een nieuw distributiepunt installeert, gebruikt u een installatiewizard die u door de beschikbare instellingen leidt. Voordat u begint, kunt u het volgende:  

-   U moet de volgende beveiligingsmachtigingen hebben om te maken en configureren van een distributiepunt:  

    -   **Lees** voor de **distributiepunt** object  

    -   **Kopiëren naar distributiepunt** voor de **distributiepunt** object  

    -   **Wijzig** voor de **Site** object  

    -   **Certificaten beheren voor implementatie van besturingssysteem** voor de **Site** object  

-   Internet Information Services (IIS) moet worden geïnstalleerd op de server die als voor het distributiepunt host fungeert. Wanneer u de sitesysteemrol installeert, kan Configuration Manager IIS installeren en configureren voor u.  

Gebruik de volgende algemene procedures te installeren of een distributiepunt te wijzigen. Zie voor meer informatie over de beschikbare configuratieopties, de [een distributiepunt configureren](#bkmk_configs) sectie van dit onderwerp.  

#### <a name="to-install-a-distribution-point"></a>Om een distributiepunt te installeren  

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Servers en sitesysteemrollen**.  

2.  Systeem distributiepuntsiterollen toevoegen aan een nieuwe of bestaande sitesysteemserver:  

    -   **Nieuwe sitesysteemserver**: Op de **Start** tabblad, in de **maken** groep, kiest u **Sitesysteemserver maken**. De wizard Sitesysteemserver maken wordt geopend.  

    -   **Bestaande sitesysteemserver**: Kies de server die u wilt installeren system distributiepuntsiterollen. Als u een server, wordt een lijst van de sitesysteemrollen die al zijn geïnstalleerd op de server weergegeven in het deelvenster met resultaten.  

         Op de **Start** tabblad, in de **Server** groep, kiest u **Sitesysteemrol toevoegen**. Hiermee opent u de wizard Sitesysteemrollen toevoegen.  

3.  Op de pagina **Algemeen** specificeert u de algemene instellingen voor de sitesysteemserver. Wanneer u het distributiepunt aan een bestaande sitesysteemserver toevoegt, verifieert u de eerder geconfigureerde waarden.  

4.  Op de **Systeemrolselectie** pagina, kiest u **distributiepunt** uit de lijst met beschikbare rollen en kies vervolgens **volgende**.  

5.  Voor de volgende pagina's van de wizard, Zie de informatie in de [een distributiepunt configureren](#bkmk_configs) sectie.  

     Bijvoorbeeld, als u naar het distributiepunt als een pull-distributiepunt installeert, kiest u **Schakel dit distributiepunt om inhoud van andere distributiepunten** en vervolgens de aanvullende configuraties die pull-distributiepunten nodig hebt.  

6.  Nadat u de wizard voltooit, wordt de siterol van distributiepunt toegevoegd aan de sitesysteemserver.  

#### <a name="to-change-a-distribution-point"></a>Een distributiepunt wijzigen  

1.  Kies in de Configuration Manager-console **beheer** >  **distributiepunten**, en selecteer vervolgens het distributiepunt dat u wilt configureren.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

3.  Gebruik de informatie in de [een distributiepunt configureren](#bkmk_configs) sectie wanneer u de eigenschappen van het distributiepunt bewerkt.  

4.  Nadat u de wijzigingen die u wilt, uw instellingen opslaan en sluiten van de eigenschappen van het distributiepunt.  

##  <a name="bkmk_manage"></a>Distributiepuntgroepen beheren  
 Distributiepuntgroepen bieden een logische groepering van distributiepunten voor inhoudsdistributie. U kunt deze groepen gebruiken om te beheren en controleren van inhoud vanaf een centrale locatie voor distributiepunten die meerdere sites omvatten. Houd rekening met het volgende:

-   U kunt een of meer distributiepunten van elke site in de hiërarchie toevoegen aan een distributiepuntgroep.  

-   U kunt een distributiepunt toevoegen aan meer dan één distributiepuntgroep.  

-   Wanneer u inhoud naar een distributiepuntgroep distribueert, distribueert Configuration Manager de inhoud naar alle distributiepunten die lid van de distributiepuntgroep zijn.  

-   Als u een distributiepunt aan de distributiepuntgroep na een initiële inhoudsdistributie toevoegt, wordt in Configuration Manager automatisch de inhoud naar het nieuwe distributiepuntlid gedistribueerd.  

-   U kunt een verzameling koppelen aan een distributiepuntgroep. Wanneer u inhoud naar die verzameling distribueert, wordt door Configuration Manager bepaalt welke distributiepuntengroepen zijn gekoppeld aan de verzameling. De inhoud wordt dan gedistribueerd naar alle distributiepunten die lid van deze distributiepuntgroepen zijn.  

    > [!NOTE]  
    >  Nadat u inhoud naar een verzameling, distribueert als u de verzameling daarna hebt gekoppeld aan een nieuwe distributiepuntgroep, u moet de inhoud distribueren naar de verzameling voordat de inhoud wordt gedistribueerd naar de nieuwe distributiepuntgroep.  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>Maken en configureren van een nieuwe distributiepuntgroep  

1.  Kies in de Configuration Manager-console **beheer** > **Distributiepuntgroepen**.  

2.  Op de **Start** tabblad, in de **maken** groep, kiest u **groep maken**.  

3.  Voer de naam en beschrijving voor de distributiepuntgroep.  

4.  Op de **verzamelingen** Kies **toevoegen**, selecteer de verzamelingen die u wilt koppelen aan de distributiepuntgroep en kies vervolgens **OK**.  

5.  Op de **leden** Kies **toevoegen**, selecteer de distributiepunten die u wilt toevoegen als leden van de distributiepuntgroep en kies vervolgens **OK**.  

6.  Kies **OK** voor het maken van de distributiepuntgroep.  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>Distributiepunten toevoegen en verzamelingen koppelen aan een bestaande distributiepuntgroep  

1.  Kies in de Configuration Manager-console **beheer** > **Distributiepuntgroepen**.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

3.  Op de **verzamelingen** Kies **toevoegen** en selecteer de verzamelingen die u wilt koppelen aan de distributiepuntgroep en kies vervolgens **OK**.  

4.  Op de **leden** Kies **toevoegen** en selecteer de distributiepunten die u wilt toevoegen als leden van de distributiepuntgroep en kies vervolgens **OK**.  

5.  Kies **OK** wijzigingen aan de distributiepuntgroep wilt opslaan.  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>Geselecteerde distributiepunten toevoegen verwijst naar een nieuwe distributiepuntgroep  

1.  Kies in de Configuration Manager-console **beheer** > **distributiepunten**, en selecteer vervolgens de distributiepunten die u wilt toevoegen aan de nieuwe distributiepuntgroep.  

2.  Op de **Start** tabblad, in de **distributiepunt** groep uit, vouw **geselecteerde Items toevoegen**, en kies vervolgens **geselecteerde Items toevoegen aan de nieuwe Distributiepuntgroep**.  

3.  Voer de naam en beschrijving voor de distributiepuntgroep.  

4.  Op de **verzamelingen** Kies **toevoegen** en selecteer de verzamelingen die u wilt koppelen aan de distributiepuntgroep en kies vervolgens **OK**.  

5.  Op de **leden** Controleer dat u wilt dat de vermelde distributiepunten toevoegen als leden van de distributiepuntgroep door Configuration Manager. Kies **toevoegen** naar de distributiepunten toevoegen en selecteer vervolgens **OK**.  

6.  Kies **OK** voor het maken van de distributiepuntgroep.  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>Verwijst naar geselecteerde distributiepunten toevoegen aan bestaande distributiepuntgroepen  

1.  Kies in de Configuration Manager-console **beheer** > **distributiepunten**, en selecteer vervolgens de distributiepunten die u wilt toevoegen aan de nieuwe distributiepuntgroep.  

2.  Op de **Start** tabblad, in de **distributiepunt** groep uit, vouw **geselecteerde Items toevoegen**, en kies vervolgens **geselecteerde Items toevoegen aan bestaande Distributiepuntgroepen**.  

3.  In de **beschikbare distributiepuntengroepen**, selecteert u de distributiepuntgroepen waaraan de geselecteerde distributiepunten als leden worden toegevoegd en kies vervolgens **OK**.  

##  <a name="bkmk_configs"></a>Een distributiepunt configureren  
 Afzonderlijke distributiepunten bieden ondersteuning voor een groot aantal verschillende configuraties. Niet alle distribution point typen ondersteunen echter alle configuraties. Cloud-gebaseerde distributiepunten ondersteunen bijvoorbeeld geen implementaties van inhoud die beschikbaar zijn voor PXE of multicast. Informatie over specifieke beperkingen kunt u vinden in de volgende onderwerpen:  

-   [Cloud-gebaseerde distributiepunt gebruiken met System Center Configuration Manager](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [Een pull-distributiepunt gebruiken met System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

De volgende secties beschrijven de configuraties die u selecteren kunt wanneer u een nieuw distributiepunt installeren of de eigenschappen van een bestaand distributiepunt te bewerken.  

### <a name="general"></a>Algemeen  
 Configureer de algemene distributiepuntinstellingen:  

-   **Installeer en Configureer IIS indien vereist door Configuration Manager**: Kies deze instelling om Configuration Manager installeren en configureren van IIS op de server, als dit nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten. Als IIS niet op de server is geïnstalleerd en u deze instelling niet selecteert, moet u IIS installeren voordat het distributiepunt correct kan worden geïnstalleerd.  

    > [!NOTE]  
    >  Deze optie is beschikbaar, alleen wanneer u een nieuw distributiepunt installeert.  

- **Inschakelen en configureren van BranchCache voor dit distributiepunt**: Kies deze instelling om Configuration Manager Windows BranchCache configureren op de distributiepuntserver. Zie voor meer informatie over het gebruik van Windows BranchCache met System Center Configuration Manager [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache) in *ondersteuning voor Windows-onderdelen en netwerken in System Center Configuration Manager*.

-   **Configureren hoe clientapparaten communiceren met het distributiepunt**: Er zijn voordelen en nadelen toe voor het gebruik van HTTP en HTTPS. Zie voor meer informatie "Aanbevolen beveiligingsprocedures voor inhoudsbeheer" in [fundamentele concepten voor content management in System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   **Clients toestaan anoniem verbinding te**: Deze instelling bepaalt u of het distributiepunt anonieme verbindingen van Configuration Manager-clients naar de Inhoudsbibliotheek toestaat.  

    > [!IMPORTANT]  
    >  Reparatie van een Windows Installer-toepassing kan op een client falen wanneer u deze instelling niet gebruikt.  
    >   
    >  Wanneer u een Windows Installer-toepassing op Configuration Manager-client implementeert, wordt in Configuration Manager het bestand naar de lokale cache op de client downloadt. De bestanden worden verwijderd nadat de installatie is voltooid.
    >  
    >  De Configuration Manager-client werkt de bronlijst voor Windows Installer voor de geïnstalleerde Windows Installer-toepassingen met het Inhoudspad voor de Inhoudsbibliotheek op gekoppelde distributiepunten. Later, als u de herstelactie vanuit een programma verwijderen of op een Configuration Manager-client start, probeert MSIExec toegang tot het Inhoudspad met een anonieme gebruiker.  
    >   
    >  U kunt echter de updates beschreven in de Microsoft Knowledge Base-artikel installeren [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) en wijzigt u een registersleutel bij om dit gedrag te wijzigen.  
    >   
    >  Nadat de update is geïnstalleerd op de clients, heeft MSIExec toegang tot het Inhoudspad met behulp van het aangemelde gebruikersaccount wanneer u er niet voor kiest de **clients toestaan anoniem verbinding te** instelling.  

-   **Maak een zelfondertekend certificaat of importeer een openbare-sleutelinfrastructuur (PKI)-clientcertificaat voor het distributiepunt**: Het certificaat heeft de volgende doeleinden:  

    -   Het verifieert het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

    -   Als u controleert de **PXE-ondersteuning inschakelen voor clients** vak op het **PXE-instellingen** pagina, wordt het certificaat verzonden naar computers die een PXE-opstartbewerking uitvoeren, zodat ze verbinding met een beheerpunt tijdens de implementatie van het besturingssysteem maken kunnen.  

    Wanneer uw beheerpunten in de site zijn geconfigureerd voor HTTP, maakt u een zelfondertekend certificaat. Importeer een PKI-clientcertificaat wanneer uw beheerpunten zijn geconfigureerd voor HTTPS.  

    Om het certificaat hebt geïmporteerd, gaat u naar een Public Key Cryptography Standard (PKCS #12) bestand met een PKI-certificaat met de volgende vereisten voor Configuration Manager:  

    -   Het bedoelde gebruik moet clientverificatie omvatten.  

    -   De persoonlijke sleutel moet exporteerbaar zijn ingeschakeld.  

    > [!TIP]  
    >  Er zijn geen specifieke vereisten voor het certificaatonderwerp of de alternatieve naam voor onderwerp (SAN); u kunt hetzelfde certificaat gebruiken voor meerdere distributiepunten.  

     Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) voor meer informatie over de certificaatvereisten.  

     Voor een Voorbeeldimplementatie van dit certificaat, Zie de sectie "Implementeren van de Client-certificaat voor distributiepunten" in [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

-   **Dit distributiepunt inschakelen voor voorbereide inhoud**: Kies deze instelling naar het distributiepunt inschakelen voor voorbereide inhoud. Als deze instelling is geselecteerd, kunt u distributiegedrag configureren wanneer u inhoud distribueert. U kunt altijd Doe het volgende:

 - De inhoud vooraf op het distributiepunt.
 - De initiële inhoud voor het pakket voor te bereiden, maar het normale inhouddistributieproces gebruiken wanneer er updates beschikbaar voor de inhoud zijn.
 - Het normale inhouddistributieproces gebruiken voor de inhoud van het pakket.  

### <a name="drive-settings"></a>Stuurprogramma-instellingen  

> [!NOTE]  
>  Deze opties zijn beschikbaar, alleen wanneer u een nieuw distributiepunt installeert.  

Geef de Stationsinstellingen voor het distributiepunt. U kunt maximaal twee schijfstations voor de Inhoudsbibliotheek en twee schijfstations voor de pakketshare configureren. Configuration Manager kan extra stations gebruiken wanneer de eerste twee de geconfigureerde stationsruimtereserve bereiken. De **Stationsinstellingen** pagina configureert de prioriteit voor de schijfstations en de hoeveelheid vrije schijfruimte die overblijft op elk schijfstation.  

-   **Gereserveerde ruimte op station (MB)**: De waarde die u voor deze instelling configureert bepaalt de hoeveelheid vrije ruimte op een station voordat Configuration Manager een ander station kiest en verdergaat met het kopieerproces naar dat station. Inhoudsbestanden kunnen meerdere stations omvatten.  

-   **Inhoudslocaties**: Geef de inhoudslocaties voor de inhoud van tapewisselaar en pakket-share. Configuration Manager kopieert inhoud naar de primaire Inhoudslocatie tot de opgegeven waarde voor de hoeveelheid vrije schijfruimte wordt bereikt **schijfruimte (MB) reserveren**. De inhoudslocaties zijn standaard ingesteld op **automatische**. De primaire Inhoudslocatie is ingesteld op het schijfstation dat de meeste schijfruimte bij de installatie heeft en de secundaire locatie wordt toegewezen aan het schijfstation dat de tweede meeste vrije schijfruimte heeft. Wanneer de primaire en secundaire stations de gereserveerde ruimte op station bereiken, wordt Configuration Manager een ander beschikbaar station met de meeste vrije schijfruimte kiest en verdergaat met het kopieerproces.  

> [!NOTE]  
>  Om te voorkomen dat Configuration Manager op een specifiek station wordt geïnstalleerd, maakt u een leeg bestand met de naam **no_sms_on_drive.sms** en kopieer het naar de hoofdmap van het station vóór u het distributiepunt installeert.  

### <a name="pull-distribution-point"></a>Pull-distributiepunt  
Als u zich **Schakel dit distributiepunt om inhoud van andere distributiepunten**, u het gedrag van hoe die computer opgehaald voor de inhoud die u naar het distributiepunt distribueert wijzigen. Er wordt een pull-distributiepunt.  

Voor elk pull-distributiepunt dat u configureert, moet u een of meer brondistributiepunten waaruit het pull-distributiepunt de inhoud opgehaald:  

-   Kies **toevoegen**, en selecteer vervolgens een of meer van de beschikbare distributiepunten als brondistributiepunten.  

-   Kies **verwijderen** het geselecteerde distributiepunt als een brondistributiepunt te verwijderen.  

-   Gebruik de pijltjesknoppen om de volgorde waarin het pull-distributiepunt contactpersonen die de bron distributiepunten wanneer het pull-distributiepunt probeert over te dragen inhoud aan te passen. Distributiepunten met de laagste waarde wordt eerst contact gemaakt met.  

### <a name="pxe"></a>PXE  
Geef op of PXE moet worden ingeschakeld op het distributiepunt. Wanneer u PXE inschakelt, installeert Configuration Manager Windows Deployment Services op de server, indien nodig. Windows Deployment Services is de service die de PXE-opstartprocedure uitvoert voor installeren van besturingssystemen. Nadat u de wizard om het distributiepunt te maken, installeert Configuration Manager een provider in Windows Deployment Services die de PXE-opstartfuncties gebruikt.  

Als u zich **PXE-ondersteuning inschakelen voor clients**, configureer de volgende instellingen:  

-   **Dit distributiepunt toestaan te reageren op binnenkomende PXE-aanvragen**: Geef op of Windows Deployment Services inschakelen zodat ze op PXE-serviceaanvragen reageren. Gebruik dit selectievakje in-en uitschakelen van de service zonder de PXE-functionaliteit van het distributiepunt verwijderen.  

-   **Schakel onbekende computerondersteuning**: Geef op of u ondersteuning wilt inschakelen voor computers die niet worden beheerd door Configuration Manager.  

-   **Een wachtwoord verplicht stellen wanneer computers PXE gebruiken**: Geef een sterk wachtwoord voor extra beveiliging voor uw PXE-implementaties.  

-   **Affiniteit tussen gebruikers en apparaten**: Geef op hoe het distributiepunt gebruikers moet koppelen aan de doelcomputer voor PXE-implementaties. Kies een van de volgende opties:  

    -   **Gebruikersaffiniteit apparaat met automatische goedkeuring toestaan**: Kies deze instelling gebruikers automatisch wilt koppelen aan de doelcomputer zonder te wachten op goedkeuring.  

    -   **Gebruikersaffiniteit apparaat in afwachting van goedkeuring door beheerder toestaan**: Kies deze instelling moet worden gewacht op goedkeuring van een gebruiker met beheerdersrechten voordat gebruikers gekoppeld aan de doelcomputer worden.  

    -   **Geen affiniteit tussen gebruikers en apparaten toestaan**: Kies deze instelling om te specificeren dat gebruikers niet gekoppeld aan de doelcomputer.  

     Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md) voor meer informatie over de gebruikersaffiniteit van het apparaat.  

-   **Netwerkinterfaces**: Geef op dat het distributiepunt reageert op PXE-aanvragen van alle netwerkinterfaces of van specifieke netwerkinterfaces. Als het distributiepunt op specifieke netwerkinterfaces reageert, moet u het MAC-adres voor elke netwerkinterface opgeven.  

-   **De Reactievertraging van de PXE-server (seconden) opgeven**: Geef in seconden op hoe lang de vertraging is voordat het distributiepunt reageert op computeraanvragen wanneer er meerdere distributiepunten met PXE-functionaliteit worden gebruikt. Standaard de Configuration Manager PXE-servicepunt antwoordt eerst PXE-aanvragen van het netwerk.  

> [!NOTE]  
>  U kunt het PXE-protocol implementaties van besturingssystemen op clientcomputers van Configuration Manager te starten. Configuration Manager gebruikt de siterol van distributiepunt met PXE-functionaliteit voor het implementatieproces van het besturingssysteem initieert. Het distributiepunt met PXE-functionaliteit moet worden geconfigureerd voor:
>
> 1. Reageren op PXE-opstartaanvragen die Configuration Manager-clients op het netwerk.
> 2. Met de Configuration Manager-infrastructuur om te bepalen welke implementatieacties te laten werken.  

### <a name="multicast"></a>Multicast  
Geef op of multicast inschakelen op het distributiepunt. Wanneer u multicast inschakelt, installeert Configuration Manager Windows Deployment Services op de server, indien nodig.  

Als u controleert de **multicast inschakelen om gelijktijdig te verzenden gegevens naar meerdere clients** Configureer de volgende instellingen:  

-   **Multicastverbindingsaccount**: Geeft de serviceaccount te gebruiken wanneer u Configuration Manager-databaseverbindingen voor multicast configureert.  

-   **Multicastadresinstellingen**: Geef de IP-adressen voor het verzenden van gegevens naar de doelcomputers. Standaard wordt het IP-adres verkregen van een DHCP-server die is ingeschakeld voor het distribueren van multicastadressen. Afhankelijk van de netwerkomgeving, kunt u een bereik met IP-adressen van 239.0.0.0 tot en met 239.255.255.255.  

    > [!IMPORTANT]  
    >  De IP-adressen die u configureert moet toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Controleer of routers en firewalls multicast-verkeer toestaan tussen de doelcomputer en de siteserver.  

-   **UDP-poortbereik voor multicast**: Geef het bereik van User Datagram Protocol (UDP)-poorten die worden gebruikt om gegevens te verzenden naar de doelcomputers.  

    > [!IMPORTANT]  
    >  De UDP-poorten moeten toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Controleer of routers en firewalls multicast-verkeer toestaan tussen de doelcomputer en de siteserver.  

-   **Overdrachtssnelheid van client**: Selecteer de overdrachtssnelheid die wordt gebruikt om gegevens te downloaden naar de doelcomputers.  

-   **Maximum aantal clients**: Geef het maximum aantal doelcomputers op dat het besturingssysteem vanaf dit distributiepunt kan downloaden.  

-   **Geplande multicast inschakelen**: Geef op hoe Configuration Manager bepaald wanneer het implementeren van besturingssystemen naar doelcomputers moet worden gestart. Configureer de volgende opties:  

    -   **Startvertraging van sessie (minuten)**: Geef het aantal minuten dat Configuration Manager wacht voordat het reageert op de eerste implementatieaanvraag.  

    -   **Minimale sessiegrootte (clients)**: Geef op hoeveel aanvragen moeten worden ontvangen voordat Configuration Manager begint met de implementatie van het besturingssysteem.  

> [!NOTE]  
>  Multicast-implementaties houden netwerkbandbreedte vrij door gegevens gelijktijdig naar meerdere Configuration Manager-clients een kopie van de gegevens verzenden naar elke client via een aparte verbinding in plaats van te verzenden. Zie voor meer informatie over het gebruik van multicast voor de implementatie van besturingssystemen, [gebruik multicast om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

### <a name="group-relationships"></a>Groepsrelaties  

> [!NOTE]  
>  Deze opties zijn beschikbaar, alleen wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

Beheren van de distributiepuntgroepen waarvan dit distributiepunt lid is.  

Kies voor dit distributiepunt als een lid toevoegen aan een bestaande een distributiepuntgroep, **toevoegen**. Selecteer een bestaand distributiepunt in de lijst in de **toevoegen aan Distributiepuntgroepen** dialoogvenster vak en kies vervolgens **OK**.  

Als dit distributiepunt uit een distributiepuntgroep verwijderen, selecteert u de distributiepuntgroep in de lijst en kies vervolgens **verwijderen**.  

### <a name="content"></a>Inhoud  

> [!NOTE]  
>  Deze opties zijn beschikbaar, alleen wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

De inhoud beheren die naar het distributiepunt is gedistribueerd. De **implementatiepakketten** sectie geeft een lijst van de pakketten die naar dit distributiepunt is gedistribueerd. U kunt een pakket in de lijst selecteren en de volgende acties uitvoeren:  

-   **Valideren**: Start het proces voor het valideren van de integriteit van de inhoudsbestanden in het pakket. De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en selecteer vervolgens de **inhoudsstatus** knooppunt.  

-   **Opnieuw distribueren**: Hiermee kopieert u alle inhoudsbestanden in het pakket naar het distributiepunt en de bestaande bestanden worden overschreven. U gebruikt deze bewerking gewoonlijk om inhoudsbestanden in het pakket te herstellen.  

-   **Verwijder**: Hiermee verwijdert de inhoudsbestanden van het distributiepunt voor het pakket.  

### <a name="content-validation"></a>Validatie van inhoud  
Geef op of het instellen van een planning voor het valideren van de integriteit van inhoudsbestanden op het distributiepunt. Wanneer u inhoudsvalidatie op een planning inschakelt, wordt Configuration Manager begint het proces op het geplande tijdstip en wordt alle inhoud op het distributiepunt gecontroleerd. U kunt ook de validatieprioriteit van de inhoud configureren. De prioriteit is standaard ingesteld op **laagste**.  

De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en selecteer vervolgens de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, software-updatepakket en installatiekopie) wordt weergegeven.  

> [!WARNING]  
>  Hoewel u de planning voor inhoudsvalidatie met behulp van de lokale tijd voor de computer opgeeft, bevat de Configuration Manager-console de planning in UTC.  

### <a name="boundary-group"></a>Grensgroep  
Beheer de grensgroepen waaraan dit distributiepunt is toegewezen. U kunt grensgroepen koppelen aan een distributiepunt. Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan het distributiepunt gebruiken als bronlocatie voor inhoud.

Aanvullend:

- Voordat u versie 1610, u kunt controleren de **clients met dit sitesysteem als een terugvalbronlocatie voor inhoud toestaan** wilt toestaan dat clients buiten deze grensgroepen terug te vallen en gebruik het distributiepunt als bronlocatie voor inhoud wanneer er geen andere distributiepunten beschikbaar zijn. Zie voor meer informatie over grensgroepen [grensgroepen voor versies 1511 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606). Zie voor voorkeursdistributiepunten, [fundamentele concepten voor content management in System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).

- Versie 1610 of hoger, configureert u grensgroep *relaties* die bepalen wanneer en op welke grensgroepen van een client terugvallen om inhoud te zoeken. Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


### <a name="schedule"></a>Planning  

> [!NOTE]  
>  Deze opties zijn beschikbaar, alleen wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

> [!TIP]  
>  Dit tabblad is alleen beschikbaar wanneer u de eigenschappen bewerkt van een distributiepunt dat extern is van de site server-computer.  

 Geef op of een planning die beperkt wanneer Configuration Manager gegevens naar het distributiepunt overdragen kan configureren.  

> [!IMPORTANT]  
>  Het schema is gebaseerd op de tijdzone van de verzendende site, niet het distributiepunt.  

Om gegevens te beperken, selecteert u de periode en kies een van de volgende instellingen voor **beschikbaarheid**:  

-   **Open voor alle prioriteiten**: Hiermee geeft u de Configuration Manager verzendt gegevens naar het distributiepunt zonder beperkingen.  

-   **Gemiddelde en hoge prioriteit toestaan**: Hiermee geeft u dat Configuration Manager alleen de gegevens over gemiddelde en hoge prioriteit naar het distributiepunt verzendt.  

-   **Alleen hoge prioriteit toestaan**: Hiermee geeft u op dat de Configuration Manager alleen hoge prioriteit gegevens naar het distributiepunt verzendt.  

-   **Gesloten**: Hiermee geeft u dat Configuration Manager geen gegevens naar het distributiepunt verzendt.  

U kunt gegevens beperken op basis van prioriteit of de verbinding gedurende geselecteerde perioden te sluiten.  

### <a name="rate-limits"></a>Frequentielimieten  

> [!NOTE]  
>  Deze opties zijn beschikbaar, alleen wanneer u de eigenschappen van een eerder geïnstalleerd distributiepunt bewerkt.  

> [!TIP]  
>  Dit tabblad is alleen beschikbaar wanneer u de eigenschappen bewerkt van een distributiepunt dat extern is van de site server-computer.  

Geef op of frequentielimieten voor het beheren van de netwerkbandbreedte die wordt gebruikt bij Configuration Manager overdracht van inhoud naar het distributiepunt moeten worden geconfigureerd. U kunt kiezen uit de volgende opties:  

-   **Onbeperkt bij verzenden naar deze bestemming**: Deze optie geeft aan dat Configuration Manager naar het distributiepunt met zonder frequentielimietbeperkingen inhoud verzendt.  

-   **Pulsemodus**: Deze optie geeft de grootte van de gegevensblokken die naar het distributiepunt worden verzonden. U kunt daarnaast een vertraging tussen het verzenden van de afzonderlijke gegevensblokken opgeven. Gebruik deze optie wanneer u gegevens via een netwerkverbinding van zeer lage bandbreedte naar het distributiepunt moet verzenden. U wellicht bijvoorbeeld beperkingen instellen om te verzenden 1 KB gegevens om de vijf seconden, ongeacht de snelheid van de koppeling of het gebruik ervan op een bepaald moment.  

-   **Beperkt tot opgegeven maximale overdrachtssnelheid per uur**: Deze instelling om een site op basis van de hoeveelheid tijd die u configureert gegevens verzenden naar een distributiepunt te laten opgeven. Als u deze optie gebruikt, wordt Configuration Manager geeft niet de beschikbare bandbreedte van het netwerk, maar verdeelt het de tijd die het verzenden van gegevens. Gegevens worden vervolgens verzonden voor een kort tijdsblok, gevolgd door tijdsblokken waarin geen gegevens worden verzonden. Bijvoorbeeld, als de maximale snelheid wordt ingesteld op **50%**, Configuration Manager brengt gegevens voor een bepaalde tijd, gevolgd door een even lange periode waarin geen gegevens worden verzonden. De werkelijke hoeveelheid gegevens, of grootte van het gegevensblok, wordt hiermee niet beheerd. Alleen de hoeveelheid tijd waarin gegevens worden verzonden, wordt beheerd.  

