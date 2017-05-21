---
title: Diagnostische gegevens voor 1702 | System Center Configuration Manager
description: Meer informatie over de niveaus van diagnoses en gebruiksgegevens die door System Center Configuration Manager versie 1702 worden verzameld.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d43ab033-2902-4681-8716-b4b17a6df372
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
ms.openlocfilehash: 0e1d93712150fb3d6fabc3f057711eba1194c3ad
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1702-of-system-center-configuration-manager"></a>Niveaus van diagnostische gegevensverzameling gebruiksgegevens voor 1702-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1702 worden drie niveaus van diagnostische en gebruiksgegevens worden verzameld: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bevatten meer informatie over gegevens die elk niveau worden verzameld.

Wijzigingen van eerdere versies worden aangegeven met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager worden niet verzameld sitecodes, sites, namen, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op de basis of uitgebreid niveaus. Een verzameling van deze informatie op het niveau van de volledige is niet purposeful, dat wil zeggen, mogelijk zijn opgenomen in de geavanceerde diagnostische gegevens zoals logboekbestanden of geheugen momentopnamen. Microsoft gebruikt deze gegevens niet geïdentificeerd, contact met u of advertenties ontwikkelen.



##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders die een op rollen gebaseerd administratief bereik met **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen diagnostische en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

U het niveau van de gegevens van de console wijzigen door te navigeren naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**. Open **hiërarchie-instellingen**, en selecteer vervolgens het gewenste niveau.  



##  <a name="bkmk_level1"></a> Niveau 1 - Basis
De op basisniveau bevat gegevens over uw hiërarchie, de gegevens die vereist zijn om te helpen verbeteren van de installatie of upgrade van de gebruikerservaring en gegevens die u helpen te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- Beheerconsole:
   - Statistieken over consoleverbindingen (versie van besturingssysteem, taal, SKU en architectuur, systeemgeheugen, het aantal logische processors, site-ID, geïnstalleerde versies van .NET en taalpakketten console verbinden)

- Eenvoudige implementatie van toepassingen en -type wordt in mindering gebracht (totaal aantal apps, totale apps met meerdere implementatietypen totale apps met afhankelijkheden totale vervangen apps en telling van implementatietechnologieën in gebruik)

- Configuration Manager site hiërarchie basisgegevens (lijst met de site, type, versie, status, aantal clients en tijdzone)

- Basic databaseconfiguratie (processors clusterconfiguratie en configuratie van gedistribueerde weergaven)

- ***[Bijgewerkt] *** Basic detectie statistieken (detectie aantal of minimum/maximum/gemiddelde groep grootten) waaronder wanneer de site volledig met Azure Active Directory Services wordt uitgevoerd.

- Basisinformatie van Endpoint Protection (antimalware-clientversies)

- Basic besturingssysteemimplementatie (OSD) wordt in mindering gebracht (afbeeldingen)

- Basic server sitesysteeminformatie (sitesysteemrollen gebruikt, via Internet en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

- Schema voor Configuration Manager-database (hash van alle objectdefinities)

- Geconfigureerde telemetrie niveau, modus (online of offline) en snel update-configuratie

- Telling van de clienttalen en landinstellingen

- Telling van Configuration Manager-clientversies en versies van besturingssystemen

- Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

- Aantal Windows 10-apparaten per branch en build

- Meetgegevens over databaseprestaties (informatie over replicatieverwerking, beste in SQL Server opgeslagen procedures op processor- en schijfgebruik)

- Distributiepunt en beheerpunten typen en basisconfiguratie informatie (beveiligde, voorbereid, PXE, multicast SSL-status pull/peer distributiepunten MDM-functionaliteit, SSL is ingeschakeld, enz.)

- Installatie-informatie:
     - Maken, installeert u type, taalpakketten, functies die u hebt ingeschakeld   

     - Gebruik van pre-release, installatietype media, vertakking type

     - Software Assurance-vervaldatum      

     - Implementatiestatus pack en fouten bijwerken, uitgevoerd en de vereiste fouten downloaden     

     - Gebruik van snelle ring update

     - Versie van na de upgrade-script

- SQL-versie, servicepack-niveau edition, sorterings-ID en tekenset     
- Telemetriestatistieken (wanneer uitgevoerd, runtimefouten)

- Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)




##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau van de verbeterde is de standaard nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in de op basisniveau en onderdeelspecifieke gegevens (frequentie en duur van gebruik), instellingen voor Configuration Manager-clients (onderdeelnaam, status en bepaalde instellingen zoals pollingintervallen) en algemene informatie over software-updates.

Dit niveau wordt aanbevolen, omdat hiermee het minimumaantal gegevens die vereist zijn nuttig verbeteringen te maken in toekomstige versies van producten en diensten van Microsoft. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), de details van de beveiligingsgerelateerde objecten of beveiligingsproblemen zoals tellingen van systemen die software-updates vereisen.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- **Toepassingsbeheer:**  

   - Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

   - App vervanging van de maximale diepte van keten

   - Toepassing goedkeuring statistieken en gebruik frequentie

   - ***[Bijgewerkt] *** Informatie over de implementatie van toepassing (gebruik van een installatie versus verwijderen, goedkeuring, gebruikersinteractie ingeschakeld/uitgeschakeld afhankelijkheid, vervanging en gebruik telling van onderdeel voor installatie van gedrag vereist)  

   - Beleid en de complexiteit statistieken

   - Statistieken over beschikbare toepassingsaanvragen

   - ***[Nieuw] *** Basic configuratiegegevens voor pakketten en programma's (implementatie-opties en programma vlaggen)

   - Informatie voor implementatietypen die worden gebruikt binnen de organisatie Basic gebruik/doelen (gebruiker ten opzichte van de apparaten die zijn gericht, versus beschikbaar en universele apps vereist)

   - Statistieken van grens (hoeveel snel, hoeveel vertragen en tellen per groep)

   - Aantal App-V-omgevingen en implementatie-eigenschappen

   - Aantal van toepassing zijnde toepassingen per besturingssysteem  

   - ***[Nieuw] *** Aantal toepassingen waarnaar wordt verwezen door een takenreeks

   - Aantal pakketten per type  

   - Aantal pakket/programma-implementaties  

   - Aantal toepassingen met een Windows 10-licentie  

   - Aantal van de Windows Store voor Business-apps en sync statistieken (inclusief samengevatte typen apps, in licentie gegeven app-status en aantal online en offline gelicentieerde apps)  

   - Type onderhoudsvenster en duur  

   - Minimum/maximum/gemiddelde aantal toepassingsimplementaties per gebruiker/apparaat gedurende een periode

   - ***[Nieuw] *** Meest voorkomende toepassing foutcodes voor clientinstallatie door implementatietechnologie

   - MSI-configuratieopties en -apparaten

   - ***[Nieuw] *** Statistieken over de interactie met de melding voor vereiste software-implementaties door de eindgebruiker   

   - Universele Access (UDA) gebruik hoe gemaakt




- **Client:**  

   - Versie van de client Active Management Technology (AMT)

   - BIOS-ouderdom in jaar

   - Automatische Clientupgrade: implementatieconfiguratie inclusief piloting en uitsluiting gebruik door clients (uitgebreide interoperabiliteit client)

   - Grootte van de clientconfiguratie cache

   - Client implementatie downloaden fouten

   - Client health statistieken en de belangrijkste probleem samenvatting

   - Melding opnieuw in te grijpen clientstatus (het aantal keren wordt uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)
   - Aantal clientinstallaties vanaf elk bronlocatietype  

   - Aantal mislukte clientinstallaties  

   - ***[Nieuw] *** Telling van apparaten die door Hyper-V- of Azure gevirtualiseerde  

   - Telling van Software Center acties   

   - ***[Nieuw] *** Telling van UEFI-apparaten

   - Implementatiemethoden gebruikt voor de client en het aantal clients per implementatiemethode

   - Lijst met en aantal ingeschakelde clientagents  

   - Besturingssysteem-ouderdom in maanden

   - Het aantal hardware-inventarisklassen, software-inventaris regels en regels voor het verzamelen

   - ***[Nieuw] *** Statistieken voor apparaat health attestation met inbegrip van de meest voorkomende fout codes, aantal lokale servers en de aantallen van apparaten in verschillende statussen.



- **Cloudservices:**

  - Statistieken voor configuratie en gebruik van Cloud Management Gateway

  - ***[Nieuw] *** Telling van clients die zijn gekoppeld aan Azure Active Directory-Services

  - Aantal verzamelingen die zijn gesynchroniseerd met de Operations Management-pakket

  - Telling van de Upgrade Analytics Connectors

  - Of de Operations Management Suite cloud-connector is ingeschakeld




- **Verzamelingen:**

    - Gebruik van verzameling-ID (niet wordt uitgevoerd buiten-id's)

    - Verzameling evaluatie statistieken (Querytijd toegewezen versus aantal niet-toegewezen, aantallen per type, de overschakeling van de ID en het gebruik van de regel)

    - Verzamelingen zonder een implementatie




- **Compatibiliteitsinstellingen:**  

    - Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    - Aantal configuratie-items per type  

    - Aantal implementaties die ingebouwde referentie-instellingen (nu vastleggen instelling herstellen)  

    - Aantal regels en implementaties die zijn gemaakt voor de aangepaste instellingen (nu vastleggen instelling herstellen)  
    -  Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP)-, VPN-, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    - Telling van SCEP-certificaat, VPN-, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - Voor Passport for Work beleid (gemaakt, geïmplementeerd)



- **Inhoud:**  

    - Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    - Groepsrelaties grens en alternatieve configuratie

    - Statistieken voor het downloaden van inhoud van client

    - Aantal grenzen per type  

    - Telling van clients voor peer-cache en statistieken voor Poortgebruik

    - Distribution Manager configuratiegegevens (threads, tussen elke poging, aantal nieuwe pogingen, en instellingen voor pull-distributiepunten)  

    - Distribution point configuratiegegevens (gebruik van de vertakking uit cache en distribution point bewaking)

    - Distribution point groepsinformatie (aantal pakketten en distributiepunten die zijn toegewezen aan elk distributiepuntgroep)  



- **Endpoint Protection:**  

   - Beleidsregels voor geavanceerde bedreiging beveiliging (vrije) (aantal beleidsregels en of beleidsregels worden geïmplementeerd)

   - Het aantal waarschuwingen die zijn geconfigureerd voor de functie Endpoint Protection  

   - Aantal verzamelingen die zijn geselecteerd om te worden weergegeven in het dashboard Endpoint Protection  

   - Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid implementeren)  

   - Endpoint Protection schadelijke software en het gebruik van Windows Firewall-beleid (het aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit bevat geen informatie over de instellingen die zijn opgenomen in het beleid.  



- **Migratie:**

  - Aantal gemigreerde objecten (gebruik van de migratiewizard)



- **Mobile Device Management (MDM):**  

    - Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, rest vastmaken wissen, buiten gebruik stellen en opdrachten nu synchroniseren

    - Aantal beleidsregels voor mobiele apparaten  

    - Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn ingeschreven (bulk, op basis van gebruikers)  

    - Telling van gebruikers met meerdere ingeschreven mobiele apparaten  

    - Planning en statistieken polling voor mobiel apparaat in duur van mobiele apparaten  




- **Microsoft Intune problemen oplossen:**

    - Aantal en de grootte van de acties voor apparaat (wissen, buiten gebruik stellen, vergrendelen) Telemetrie en berichten van gegevens die worden gerepliceerd naar Microsoft Intune

    - Aantal en de grootte van status, status, inventaris, RDR, DDR, UDX, Tenant statusberichten, POL, logboek Cert, CRP, Resync, CFD, RDO, BEX, console en naleving die worden gedownload van Microsoft Intune

    - Volledige en delta-synchronisatie gebruikersstatistieken voor Microsoft Intune



- **Lokaal Mobile Device Management (MDM)**  

    - Aantal Windows 10-bulkregistratiepakketten en -profielen  

    - Statistieken over geslaagde/mislukte lokale MDM-toepassingsimplementaties  




- **Implementatie van besturingssysteem:**  

    - Aantal opstartinstallatiekopieën, stuurprogramma's, stuurprogrammapakketten, distributiepunten met ingeschakelde multicast, distributiepunten voor PXE-functionaliteit en takenreeksen  

    - Telling van edition upgrade beleid

    - Telt het aantal taak volgorde stap verbruik



- **Site-updates:**

    - Versies van geïnstalleerde Configuration Manager-hotfixes



- **Software-updates:**  

    - Beschikbaar en deadline delta's die worden gebruikt in de regels voor automatische implementatie  

    - Gemiddeld en maximumaantal toewijzingen per update  

    - Evaluatie van client-updates en scanplanningen  

    - Classificaties die worden gesynchroniseerd door Software-updatepunt

    - Statistieken over clusterpatching  

    - Configuratie van Windows 10 express-updates

    - Configuraties die worden gebruikt voor actieve Windows 10-onderhoudsplannen  

    - Aantal geïmplementeerde Office 365-updates  

    - Aantal updategroepen en toewijzingen  

    - Aantal pakketten van en het minimum/maximum/gemiddelde aantal distributiepunten die zijn gericht aan pakketten  

    - Telling van updates die zijn gemaakt en geïmplementeerd met System Center updates Publisher  

    - Telling van Windows 10-clients die Windows Update voor bedrijven gebruiken  

    - Aantal regels voor automatische implementatie die zijn gerelateerd aan synchronisatie  

    - Aantal regels voor automatische implementatie waarmee nieuwe updates worden gemaakt of waarmee updates worden toegevoegd aan een bestaande groep  

    - Aantal regels voor automatische implementatie met meerdere implementaties  
    - Aantal updategroepen en minimaal/maximaal/gemiddeld aantal updates per groep  

    - Aantal updates en het percentage van de updates die zijn geïmplementeerd, is verlopen, vervangen gedownload en gebruiksrechtovereenkomsten bevatten  

    - Software-update-punt load balancing-statistieken

    - Synchronisatieplanning voor software-updatepunten  

    - Totaal aantal/gemiddelde aantal verzamelingen die beschikken over software-update-implementaties en de maximale/gemiddelde aantal geïmplementeerde updates  

    - Foutcodes voor updatescans en het aantal computers  

    - Versies van Windows 10-dashboardinhoud  



- **SQL/prestatiegegevens:**  

    - ***[Nieuw] *** Configuratie en de duur van de site-samenvatting

    - Aantal van de grootste databasetabellen  

    - Detectie operationele statistieken (aantal objecten gevonden)

    - Detectie-typen ingeschakeld en planning (volledig, incrementele)

    - SQL AlwaysOn-informatie, gebruik en status van de replicastatus

    - SQL bijhouden prestatieproblemen, bewaarperiode of status automatisch opschonen

    - Bewaarperiode voor het SQL bijhouden

    - ***[Nieuw] *** Status en -status bericht prestatiestatistieken, met inbegrip van de meest voorkomende en meest dure berichttypen



- **Diverse**

    - ***[Nieuw] *** Configuratie van datawarehouse Service gegevenspunt met inbegrip van planning en gemiddelde synchronisatietijd

    - Telling van sites met Wake op Lan (WOL)

    - Gebruiks- en rapportages  



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau van de volledige bevat alle gegevens in de Basic en verbeterde niveaus. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates.  Dit niveau kan ook geavanceerde diagnostische gegevens zoals systeembestanden en geheugen momentopnamen, waaronder persoonlijke gegevens die beschikbaar in geheugen of logboekbestanden ten tijde van het vastleggen waren.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- Informatie over de evaluatieplanning voor regels voor automatische implementatie

- Samenvatting van de vrije status

- Evaluatie van verzamelingen en vernieuwingsstatistieken

- Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid sjabloon configuratiedetails telling van groepen die zijn verlopen software-updates

- DCM-configuratie pack voor System Center Configuration Manager-gebruik

- Gedetailleerde client implementatie installatiefouten
- Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

- Endpoint Protection-beleidsconfiguratie

- ***[Nieuw] *** Lijst met processen die zijn geconfigureerd met installatiegedrag voor toepassingen

- Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

- Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

- Minimaal/maximaal/gemiddeld aantal software-updates per pakket

- MSI-productcode (algemene apps die klanten implementeren)

- Algemene naleving van software-update-implementaties

- Aantal fouten en foutcodes voor software-update-implementaties

- Implementatiegegevens van software-update (percentage van de implementaties die zijn gericht aan client ten opzichte van de UTC-tijd vereist optionele ten opzichte van de achtergrond en opnieuw opstarten onderdrukken)

- Software-update producten gesynchroniseerd door Software-updatepunt

- Percentage van geslaagde software-updatescans

- Top 50 CPU's in de omgeving

- Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

- Windows Store voor meer informatie Business-toepassing (niet-samengestelde lijst gesynchroniseerde toepassingen, waaronder AppID, online status of offlinestatus en totaal aantal aangeschafte licenties tellingen)

