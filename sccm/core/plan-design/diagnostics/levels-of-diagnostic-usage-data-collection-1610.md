---
title: Diagnostische gegevens voor 1610 | System Center Configuration Manager
description: Meer informatie over de niveaus van diagnoses en gebruiksgegevens die door System Center Configuration Manager versie 1610 worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb20eb90-bcc0-41de-bfea-638ea470c0dd
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ba1e53fdc895690bb958c12d59f82a26067ecad3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1610-of-system-center-configuration-manager"></a>Niveaus van diagnostische gegevensverzameling gebruiksgegevens voor 1610-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1610 worden drie niveaus van diagnostische en gebruiksgegevens worden verzameld: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bevatten meer informatie over gegevens die elk niveau worden verzameld.

Wijzigingen van eerdere versies worden aangegeven met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager worden niet verzameld sitecodes, sites, namen, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op de basis of uitgebreid niveaus. Een verzameling van deze informatie op het niveau van de volledige is niet purposeful, dat wil zeggen, mogelijk zijn opgenomen in de geavanceerde diagnostische gegevens zoals logboekbestanden of geheugen momentopnamen. Microsoft gebruikt deze gegevens niet geïdentificeerd, contact met u of advertenties ontwikkelen.

##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders die een op rollen gebaseerd administratief bereik met **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen diagnostische en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

Vanaf versie 1610, u het niveau van de gegevens van de console wijzigen door te navigeren naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**. Open **hiërarchie-instellingen**, en selecteer vervolgens het gewenste niveau.  

##  <a name="bkmk_level1"></a> Niveau 1 - Basis
 De op basisniveau bevat gegevens over uw hiërarchie, de gegevens die vereist zijn om te helpen verbeteren van de installatie of upgrade van de gebruikerservaring en gegevens die u helpen te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

 Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:


-   Installatie-informatie:
       - Maken, installeert u type, taalpakketten, functies die u hebt ingeschakeld  

       - Implementatiestatus pack en fouten bijwerken, uitgevoerd en de vereiste fouten downloaden     

       - Versie van na de upgrade-script

       - Gebruik van snelle ring update

    - ***[Nieuw] *** Voorlopige gebruik, installatietype media, vertakking type

    - ***[Nieuw] *** Software Assurance-vervaldatum

- Meetgegevens over databaseprestaties (informatie over replicatieverwerking, beste in SQL Server opgeslagen procedures op processor- en schijfgebruik)

- Basic databaseconfiguratie (processors clusterconfiguratie en configuratie van gedistribueerde weergaven)

- Schema voor Configuration Manager-database (hash van alle objectdefinities)

- Telling van Configuration Manager-clientversies en versies van besturingssystemen

- Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

- Telling van de clienttalen en landinstellingen

- Aantal Windows 10-apparaten per branch en build

- Configuration Manager site hiërarchie basisgegevens (lijst met de site, type, versie, status, aantal clients en tijdzone)

- Basic server sitesysteeminformatie (sitesysteemrollen gebruikt, via Internet en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

- Basic detectie gebruikersstatistieken (gebruiker detectie aantal of minimum/maximum/gemiddelde groep grootten)

- Basisinformatie van Endpoint Protection (antimalware-clientversies)

- Eenvoudige implementatie van toepassingen en -type wordt in mindering gebracht (totaal aantal apps, totale apps met meerdere implementatietypen totale apps met afhankelijkheden totale vervangen apps en telling van implementatietechnologieën in gebruik)

- Basic besturingssysteemimplementatie (OSD) wordt in mindering gebracht (afbeeldingen)

- Distributiepunt en beheerpunten typen en basisconfiguratie informatie (beveiligde, voorbereid, PXE, multicast SSL-status pull/peer distributiepunten MDM-functionaliteit, SSL is ingeschakeld, enz.)

- Telemetriestatistieken (wanneer uitgevoerd, runtimefouten)

- Geconfigureerde telemetrie niveau, modus (online of offline) en snel update-configuratie

- Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)
- Beheerconsole:

     - Statistieken over consoleverbindingen (versie van besturingssysteem, taal, SKU en architectuur, systeemgeheugen, het aantal logische processors, site-ID, geïnstalleerde versies van .NET en taalpakketten console verbinden)    

- SQL-versie, servicepack-niveau edition, sorterings-ID en tekenset


##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau van de verbeterde is de standaard nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in de op basisniveau en onderdeelspecifieke gegevens (frequentie en duur van gebruik), instellingen voor Configuration Manager-clients (onderdeelnaam, status en bepaalde instellingen zoals pollingintervallen) en algemene informatie over software-updates.

Dit niveau wordt aanbevolen, omdat hiermee het minimumaantal gegevens die vereist zijn nuttig verbeteringen te maken in toekomstige versies van producten en diensten van Microsoft. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), de details van de beveiligingsgerelateerde objecten of beveiligingsproblemen zoals tellingen van systemen die software-updates vereisen.

Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:

-   **Toepassingsbeheer:**  

    -    Informatie voor implementatietypen die worden gebruikt binnen de organisatie Basic gebruik/doelen (gebruiker ten opzichte van de apparaten die zijn gericht, versus beschikbaar en universele apps vereist)  

    -   Informatie over de implementatie van toepassingen (Installeer/Verwijder, goedkeuring, gebruikersinteractie ingeschakeld/uitgeschakeld, afhankelijkheden en vervanging vereist)  

    -   Statistieken over beschikbare toepassingsaanvragen  

    -   Aantal pakketten per type  

    -   Aantal van toepassing zijnde toepassingen per besturingssysteem  

    -   Aantal pakket/programma-implementaties  

    -   Aantal App-V-omgevingen en implementatie-eigenschappen  

    -   Aantal toepassingen met een Windows 10-licentie  

    -   Minimum/maximum/gemiddelde aantal toepassingsimplementaties per gebruiker/apparaat gedurende een periode

    -   Type onderhoudsvenster en duur  

    -  Beleid en de complexiteit statistieken

    - ***[Bijgewerkt] *** Aantal van de Windows Store voor Business-apps en sync statistieken (inclusief samengevatte typen apps, in licentie gegeven app-status en aantal online en offline gelicentieerde apps)  

    - Statistieken van grens (hoeveel snel, hoeveel vertragen en tellen per groep)

    - MSI-configuratieopties en -apparaten

    - Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

    - App vervanging van de maximale diepte van keten

    - Universele Access (UDA) gebruik hoe gemaakt

    - ***[Nieuw] *** Toepassing goedkeuring statistieken en gebruik frequentie



-   **Client:**  

    -   Lijst met en aantal ingeschakelde clientagents  

    -   Aantal clientinstallaties vanaf elk bronlocatietype  

    -   Aantal mislukte clientinstallaties  

    -  ***[Bijgewerkt] *** Automatische Clientupgrade: implementatieconfiguratie inclusief piloting en uitsluiting gebruik door clients (uitgebreide interoperabiliteit client)

    -  Client health statistieken en de belangrijkste probleem samenvatting

    - BIOS-ouderdom in jaar

    - Besturingssysteem-ouderdom in maanden

    - Telling van Software Center acties

    - Versie van de client Active Management Technology (AMT)

    - Client implementatie downloaden fouten

    - Melding opnieuw in te grijpen clientstatus (het aantal keren wordt uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)

    - Implementatiemethoden gebruikt voor de client en het aantal clients per implementatiemethode

    - Grootte van de clientconfiguratie cache

    - ***[Nieuw] *** Aantal hardware-inventarisklassen, software-inventaris regels en regels voor het verzamelen




- **Cloudservices:**

  - Aantal verzamelingen die zijn gesynchroniseerd met de Operations Management-pakket

  -  Of de Operations Management Suite cloud-connector is ingeschakeld

  - ***[Nieuw] *** Statistieken voor configuratie en gebruik van Cloud Management Gateway

  - ***[Nieuw] *** Telling van de Upgrade Analytics Connectors




- **Verzamelingen:**

    -  Verzameling evaluatie statistieken (Querytijd toegewezen versus aantal niet-toegewezen, aantallen per type, de overschakeling van de ID en het gebruik van de regel)

    - Verzamelingen zonder een implementatie

    - Gebruik van verzameling-ID (niet wordt uitgevoerd buiten-id's)



-   **Compatibiliteitsinstellingen:**  

    -   Aantal configuratie-items per type  

    -   Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    -   Aantal implementaties die ingebouwde referentie-instellingen (nu vastleggen instelling herstellen)  

    -   Aantal regels en implementaties die zijn gemaakt voor de aangepaste instellingen (nu vastleggen instelling herstellen)  
    -   Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP)-, VPN-, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    -  Telling van SCEP-certificaat, VPN-, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - Voor Passport for Work beleid (gemaakt, geïmplementeerd)



-   **Inhoud:**  

    -   Aantal grenzen per type  

    -   Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    - ***[Nieuw] *** Grens groepsrelaties en alternatieve configuratie

    -   Distribution point groepsinformatie (aantal pakketten en distributiepunten die zijn toegewezen aan elk distributiepuntgroep)  

    -   Distribution point configuratiegegevens (gebruik van de vertakking uit cache en distribution point bewaking)  

    -   Distribution Manager configuratiegegevens (threads, tussen elke poging, aantal nieuwe pogingen, en instellingen voor pull-distributiepunten)  

    - ***[Nieuw] *** Telling van clients voor peer-cache en statistieken voor Poortgebruik

    - ***[Nieuw] *** Client downloaden van inhoud statistieken


-   **Endpoint Protection:**  

    -   Endpoint Protection schadelijke software en het gebruik van Windows Firewall-beleid (het aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit bevat geen informatie over de instellingen die zijn opgenomen in het beleid.  

    -   Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid implementeren)  

    -   Aantal verzamelingen die zijn geselecteerd om te worden weergegeven in het dashboard Endpoint Protection  

    -   Het aantal waarschuwingen die zijn geconfigureerd voor de functie Endpoint Protection  

    -     Beleidsregels voor geavanceerde bedreiging beveiliging (vrije) (aantal beleidsregels en of beleidsregels worden geïmplementeerd)


- **Migratie:**

  -   Aantal gemigreerde objecten (gebruik van de migratiewizard)



-   **Mobile Device Management (MDM):**  

    -   ***[Bijgewerkt] *** Tellen van mobiele apparaten acties uitgegeven: vergrendelen, rest vastmaken wissen, buiten gebruik stellen en opdrachten nu synchroniseren  

    -   Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn ingeschreven (bulk, op basis van gebruikers)  

    -   Planning en statistieken polling voor mobiel apparaat in duur van mobiele apparaten  

    -   Aantal beleidsregels voor mobiele apparaten  

    -   Telling van gebruikers met meerdere ingeschreven mobiele apparaten  

-   **Microsoft Intune problemen oplossen:**

    -   Aantal en de grootte van status, status, inventaris, RDR, DDR, UDX, Tenant statusberichten, POL, logboek Cert, CRP, Resync, CFD, RDO, BEX, console en naleving die worden gedownload van Microsoft Intune

    -   Aantal en de grootte van de acties voor apparaat (wissen, buiten gebruik stellen, vergrendelen) Telemetrie en berichten van gegevens die worden gerepliceerd naar Microsoft Intune

    -   Volledige en delta-synchronisatie gebruikersstatistieken voor Microsoft Intune


-   **Lokaal Mobile Device Management (MDM)**  

    -   Statistieken over geslaagde/mislukte lokale MDM-toepassingsimplementaties  

    -   Aantal Windows 10-bulkregistratiepakketten en -profielen  



-   **Implementatie van besturingssysteem:**  

    -   Aantal opstartinstallatiekopieën, stuurprogramma's, stuurprogrammapakketten, distributiepunten met ingeschakelde multicast, distributiepunten voor PXE-functionaliteit en takenreeksen  

    -   Telt het aantal taak volgorde stap verbruik

    - ***[Nieuw] *** Aantal edition upgrade beleid



-   **Site-updates:**

    - Versies van geïnstalleerde Configuration Manager-hotfixes




-   **Software-updates:**  

    -   Totaal aantal/gemiddelde aantal verzamelingen die beschikken over software-update-implementaties en de maximale/gemiddelde aantal geïmplementeerde updates  

    -   Aantal regels voor automatische implementatie die zijn gerelateerd aan synchronisatie  

    -   Aantal regels voor automatische implementatie waarmee nieuwe updates worden gemaakt of waarmee updates worden toegevoegd aan een bestaande groep  

    -   Beschikbaar en deadline delta's die worden gebruikt in de regels voor automatische implementatie  

    -   Gemiddeld en maximumaantal toewijzingen per update  

    -   Telling van updates die zijn gemaakt en geïmplementeerd met System Center updates Publisher  

    -   Aantal updategroepen en toewijzingen  

    -   Aantal pakketten van en het minimum/maximum/gemiddelde aantal distributiepunten die zijn gericht aan pakketten  

    -   Aantal updategroepen en minimaal/maximaal/gemiddeld aantal updates per groep  

    -   Aantal updates en het percentage van de updates die zijn geïmplementeerd, is verlopen, vervangen gedownload en gebruiksrechtovereenkomsten bevatten  

    -   Foutcodes voor updatescans en het aantal computers  

    -   Evaluatie van client-updates en scanplanningen  

    -   Synchronisatieplanning voor software-updatepunten  

    -   Aantal regels voor automatische implementatie met meerdere implementaties  

    -   Configuraties die worden gebruikt voor actieve Windows 10-onderhoudsplannen  

    -   Versies van Windows 10-dashboardinhoud  

    -   Telling van Windows 10-clients die Windows Update voor bedrijven gebruiken  

    -   Statistieken over clusterpatching  

    -   Aantal geïmplementeerde Office 365-updates  

    -   Classificaties die worden gesynchroniseerd door Software-updatepunt

    -   Software-update-punt load balancing-statistieken

    -  ***[Nieuw] *** Configuratie van Windows 10 express updates




-   **SQL/prestatiegegevens:**  

    -   Aantal van de grootste databasetabellen  

    -   ***[Bijgewerkt] *** SQL AlwaysOn-informatie, gebruik en status van de replicastatus

    -  Bewaarperiode voor het SQL bijhouden

    - Detectie-typen ingeschakeld en planning (volledig, incrementele)

    - Detectie operationele statistieken (aantal objecten gevonden)

    - SQL bijhouden prestatieproblemen, bewaarperiode of status automatisch opschonen



- **Diverse**

    - Telling van sites met Wake op Lan (WOL)

    - ***[Nieuw] *** Rapportages gebruik en de prestaties  



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau van de volledige bevat alle gegevens in de Basic en verbeterde niveaus. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates.  Dit niveau kan ook geavanceerde diagnostische gegevens zoals systeembestanden en geheugen momentopnamen, waaronder persoonlijke gegevens die beschikbaar in geheugen of logboekbestanden ten tijde van het vastleggen waren.

Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:

-   Evaluatie van verzamelingen en vernieuwingsstatistieken

-   Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

-   Endpoint Protection-beleidsconfiguratie

-   Implementatiegegevens van software-update (percentage van de implementaties die zijn gericht aan client ten opzichte van de UTC-tijd vereist optionele ten opzichte van de achtergrond en opnieuw opstarten onderdrukken)

-   Algemene naleving van software-update-implementaties

-   Informatie over de evaluatieplanning voor regels voor automatische implementatie

-   Aantal fouten en foutcodes voor software-update-implementaties

-   Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

-   Telling van groepen die zijn verlopen software-updates

-   Minimaal/maximaal/gemiddeld aantal software-updates per pakket

-   Percentage van geslaagde software-updatescans

-   Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

-    Software-update producten gesynchroniseerd door Software-updatepunt
-    Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid configuratiedetails van sjabloon

-    Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

-   Top 50 CPU's in de omgeving

-   DCM-configuratie pack voor System Center Configuration Manager-gebruik

-   MSI-productcode (algemene apps die klanten implementeren)

-   Samenvatting van de vrije status

-   Gedetailleerde client implementatie installatiefouten

- ***[Nieuw] *** Windows Store voor meer informatie Business-toepassing (niet-samengestelde lijst gesynchroniseerde toepassingen, waaronder AppID, online status of offlinestatus en totaal aantal aangeschafte licenties tellingen)

