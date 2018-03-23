---
title: Diagnostische gegevens en gebruiksgegevens voor 1802
titleSuffix: Configuration Manager
description: Meer informatie over de niveaus van diagnostische gegevens en gebruiksgegevens in versie 1802 verzameld.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29dd51b8-6576-4010-81ba-3129ed2c3421
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
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
ms.openlocfilehash: 4f5076b00a097500955b47938294e8a953231eaf
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1802-of-system-center-configuration-manager"></a>Niveaus van diagnostische gebruiksgegevens verzamelen van gegevens voor 1802-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager versie 1802 verzamelt drie niveaus van diagnostische gegevens en gebruiksgegevens: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bieden aanvullende details over de gegevens die op elk niveau worden verzameld.

Wijzigingen van vorige versies worden vermeld met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager biedt geen sitecodes, namen van sites, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen verzamelen over de niveaus basis of uitgebreid. Een verzameling van deze informatie op het niveau volledig is niet doelgericht. Het is mogelijk opgenomen in de geavanceerde diagnostische gegevens, zoals logboekbestanden of momentopnamen van het geheugen. Microsoft biedt geen gebruik van deze informatie voor u te identificeren, contact met u of reclame ontwikkelen.



##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders met een op rollen gebaseerd administratief bereik dat omvat **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen voor diagnostische gegevens en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

U wijzigt het niveau van de gegevens-verzameling van binnen de console door te navigeren naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**. Open **hiërarchie-instellingen**, en selecteer vervolgens de niveau van de gegevens die u wilt gebruiken.  



##  <a name="bkmk_level1"></a> Niveau 1 - Basis
Het niveau basis omvat gegevens over uw hiërarchie, de gegevens die vereist zijn om u te helpen verbeteren van de installatie of upgrade-ervaring en gegevens die u helpt te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

Voor Configuration Manager versie 1802 omvat dit niveau de volgende gegevens:

- Statistieken over verbindingen van Configuration Manager-console: Versie van het besturingssysteem, taal, SKU en architectuur, het systeemgeheugen aantal logische processors, verbinden site-ID, geïnstalleerde versies van .NET en taalpakketten console

- Basic toepassing en implementatietype Typ aantallen: totaal apps, totaalaantal apps met meerdere implementatietypen, totaalaantal apps met afhankelijkheden, totaalaantal vervangen apps en het aantal implementatietechnologieën dat in gebruik

- Configuration Manager site hiërarchie basisgegevens: site-lijst, type, versie, status, aantal clients en tijdzone

- Elementaire databaseconfiguratie: processors, clusterconfiguratie en configuratie van gedistribueerde weergaven

- Statistieken over gebruikersdetectie Basic: aantal gedetecteerde, minimale/maximale/gemiddelde groepsgrootten, en wanneer de site wordt uitgevoerd met de Azure Active Directory Services

- Endpoint Protection-basisinformatie over antimalwareclients

- OS-basisimplementatie telt van installatiekopieën

- Basic site server systeemgegevens: site sitesysteemrollen gebruikt, internet en SSL status, besturingssysteem, processors, fysieke of virtuele machine en gebruik van hoge beschikbaarheid voor site

- Configuration Manager-databaseschema (hash van alle objectdefinities)

- Geconfigureerde telemetrie niveau, online of offline-modus en snelle update-configuratie

- Aantal clienttalen en landinstellingen

- Telling van Configuration Manager-clientversies, OS-versies en versies van Office

- Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

- Aantal Windows 10-apparaten per branch en build

- ***[Verplaatst]***  Aantal Windows 10-clients die gebruikmaken van Windows Update voor bedrijven  

- Maatstaven voor prestaties van de database: replicatie voor het verwerken van gegevens, bovenste procedures voor het SQL Server opgeslagen door de processor en het schijfgebruik

- Distributiepunt- en beheerpunttypen en basisinformatie over de configuratie: beveiligd, voorbereid, PXE, multicast, SSL-status, pull/peer-distributiepunten, MDM-functionaliteit en SSL zijn ingeschakeld

- Hash van de lijst met uitbreidingen voor wizards en eigenschappenvensters Administrator-console

- Installatie-informatie:
     - Bouwen, installeert u type, taalpakketten, functies die u hebt ingeschakeld   

     - Gebruik van de voorlopige versie, installatietype media, vertakking type

     - Software Assurance-vervaldatum      

     - Update pack Implementatiestatus en fouten, downloaden de voortgang en fouten in de vereisten     

     - Gebruik van de update snelle-ring

     - Versie van na de upgrade-script

- SQL-versie, servicepackniveau edition, sorterings-ID en tekenset     

- Telemetrie-statistieken: wanneer uitgevoerd, fouten

- Hiermee wordt aangegeven of de netwerkdetectie is ingeschakeld of uitgeschakeld

- ***[Verplaatst]***  Telling van clients die zijn gekoppeld aan Azure Active Directory

- ***[Nieuw]***  Aantal gefaseerde implementaties die zijn gemaakt door het type

- ***[Nieuw]***  Telling van clients voor uitgebreide interoperabiliteit

- ***[Nieuw]***  Hashed lijst met hardware-inventarisatie-eigenschappen die langer zijn dan 255 tekens



##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau uitgebreid is de standaardinstelling nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het niveau basis en functiespecifieke gegevens (frequentie en duur van gebruik), Configuration Manager-clientinstellingen (onderdeelnaam, status en bepaalde instellingen zoals polling-intervallen) en basisgegevens over software-updates.

Dit niveau wordt aanbevolen omdat u Microsoft de minimumhoeveelheid gegevens die vereist zijn biedt om nuttige verbeteringen in toekomstige versies van producten en services. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), details van beveiliging gerelateerde objecten of over beveiligingsproblemen zoals het aantal systemen waarvoor software-updates.

Voor Configuration Manager versie 1802 omvat dit niveau de volgende gegevens:

### <a name="application-management"></a>Toepassingsbeheer  

   - Appvereisten: telling van de ingebouwde voorwaarden waarnaar wordt verwezen door implementatietechnologie

   - App vervanging van de maximale diepte van een keten van

   - Toepassing goedkeuring statistische gegevens en gebruiksgegevens frequentie

   - Statistieken Inhoudsgrootte

   - Informatie over de implementatie van toepassing: het gebruik van installeren en verwijderen, vereist goedkeuring, gebruikersinteractie ingeschakeld/uitgeschakeld, afhankelijkheid, vervanging en gebruik telling van de functie voor gedrag  

   - Beleid omvang en complexiteit statistieken

   - Statistieken over beschikbare toepassingsaanvragen

   - Basisinformatie over de configuratie voor pakketten en programma's: implementatie-opties en programma-vlaggen

   - Over Basic gebruik/targeting voor implementatietypen: gebruiker versus apparaat, vereist versus beschikbaar en universele apps

   - Aantal App-V-omgevingen en implementatie-eigenschappen

   - Telling van toepassing zijnde toepassingen per besturingssysteem  

   - Telling van de toepassingen waarnaar wordt verwezen door een takenreeks

   - Aantal afzonderlijke huisstijl voor application catalog

   - Telling van Office 365-toepassingen die zijn gemaakt met behulp van dashboard

   - Aantal pakketten per type  

   - Aantal pakket/programma-implementaties  

   - Aantal toepassingen met een Windows 10-licentie  

   - Telling van Windows Installer implementatietypen die door verwijderen de instellingen van inhoud

   - Telling van Microsoft Store voor bedrijven-apps en sync statistische gegevens: typen apps, gelicentieerde app-status en aantal online samengevat en offline gelicentieerde apps  

   - Type onderhoudsvenster en duur  

   - Minimaal/maximaal/gemiddeld aantal toepassingsimplementaties per gebruiker/apparaat gedurende een periode

   - Meest voorkomende toepassing foutcodes voor clientinstallatie door implementatietechnologie

   - MSI-configuratieopties en aantallen

   - Statistieken over eindgebruikers interactie met de melding voor vereiste software-implementaties   

   - Universal Data Access-gebruik, hoe gemaakt

   - ***[Nieuw]***  Gebruikersapparaataffiniteit geaggregeerd statistieken 

   - ***[Nieuw]***  Max en de gemiddelde primaire gebruikers per apparaat


### <a name="client"></a>Client  

   - Versie van de client Active Management Technology (AMT)

   - BIOS-leeftijd in jaren

   - Telling van apparaten met Secure Boot is ingeschakeld

   - Telling van apparaten op TPM-status

   - Automatische Clientupgrade: implementatieconfiguratie, met inbegrip van de client testen en de uitsluiting gebruik (uitgebreide interoperabiliteit client)

   - Grootte van de clientconfiguratie-cache

   - Client-implementatiefouten downloaden

   - Client health statistieken en samenvatting van het bovenste probleem

   - Melding bewerking actie clientstatus: het aantal keren wordt uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie

   - Aantal clientinstallaties vanaf elk bronlocatietype  

   - Aantal mislukte clientinstallaties  

   - Telling van apparaten die door Hyper-V- of Azure gevirtualiseerd  

   - Telling van Software Center-acties   

   - Telling van UEFI-apparaten

   - Implementatiemethoden voor client en de telling van clients per implementatiemethode gebruikt

   - Lijst met en aantal ingeschakelde clientagents  

   - OS-ouderdom in maanden

   - Het aantal hardware-inventarisklassen, software-inventaris regels en regels voor het verzamelen

   - Statistieken voor health attestation van apparaten: meest voorkomende foutcodes, aantal van on-premises servers en het aantal apparaten in verschillende statussen

   - ***[Nieuw]***  Aantal apparaten op standaardbrowser


### <a name="cloud-services"></a>Cloud Services  

  - Azure Active Directory discovery-statistieken

  - Statistieken voor configuratie en gebruik van Cloud Management Gateway: aantal regio's en omgevingen en -verificatie/autorisatie-statistieken

  - Telling van Azure Active Directory-toepassingen en services die zijn verbonden aan Configuration Manager

  - Aantal verzamelingen die zijn gesynchroniseerd met Operations Management Suite

  - Telling van de Upgrade Analytics Connectors

  - Hiermee wordt aangegeven of de cloud-connector van Operations Management Suite is ingeschakeld


### <a name="co-management"></a>Co-management  
  - Gebruiksstatistieken van CO management geaggregeerd: aantal ingeschreven clients, clients beleid ontvangen werkbelasting statussen, test/uitsluiting verzameling grootten en fouten met de inschrijving  

  - Telling van clients door mede beheermethode voor inschrijving  

  - Foutenstatistieken voor de inschrijving van CO-management  

  - Planning voor inschrijving en historische statistieken  

  - Telling van clients die in aanmerking komen voor CO-management  

  - Gekoppelde Microsoft Intune-tenant


### <a name="collections"></a>Verzamelingen  

   - Verzameling-ID-syntaxis (wordt niet uitgevoerd buiten de id's)

   - Verzameling evaluatie statistieken: querytijd, toegewezen en niet-toegewezen aantallen geteld met type, de overschakeling van de ID en het gebruik van de regel

   - Verzamelingen zonder een implementatie


### <a name="compliance-settings"></a>Instellingen voor naleving  

  - Basislijninformatie over basisconfiguratie: aantal, aantal implementaties en aantal verwijzingen

  - Fout van de nalevingsstatistieken-beleid

  - Aantal configuratie-items per type  

  - Aantal implementaties die verwijzen naar ingebouwde instellingen, inclusief instelling herstellen  

  - Aantal regels en implementaties die zijn gemaakt voor de aangepaste instellingen, inclusief instelling herstellen  

  - Aantal geïmplementeerde Simple Certificate Enrollment Protocol (SCEP), VPN, Wi-Fi, certificaat (.pfx) en sjablonen voor naleving

  - Telling van SCEP-certificaat, VPN, Wi-Fi, certificaat (.pfx) en naleving beleidsimplementaties per platform

  - Windows Hello voor bedrijven-beleid (gemaakt, geïmplementeerd)


### <a name="content"></a>Inhoud  

  - ***[Bijgewerkt]***  Grens beheergroep statistieken: hoeveel snel, hoeveel vertragen, aantal per groep en terugval relaties

  - Informatie over de grensgroep: aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep  

  - Groepsrelaties grens en alternatieve configuratie

  - Statistieken voor het downloaden van inhoud van client

  - Aantal grenzen per type  

  - Telling van peer-cacheclients, gebruik statistiek en statistieken met gedeeltelijke downloaden

  - Distribution Manager configuratie-informatie: threads, vertraging, aantal nieuwe pogingen, en het pull-distributiepuntinstellingen  

  - Distribution point-configuratie-informatie: het gebruik van vertakkingscache en distribution point-bewaking

  - Informatie over distributiepunten: aantal pakketten en distributiepunten die zijn toegewezen aan elke distributiepuntengroep  


### <a name="endpoint-protection"></a>Endpoint Protection  

   - Beleidsregels voor Windows Defender Advanced Threat Protection (ATP): aantal beleidsregels, en of de beleidsregels worden geïmplementeerd

   - Aantal waarschuwingen die zijn geconfigureerd voor Endpoint Protection-functie  

   - Aantal verzamelingen die zijn geselecteerd worden weergegeven in de Endpoint Protection-dashboard  

   - Telling van Windows Defender misbruiken Guard beleidsregels, implementaties en gerichte clients

   - Endpoint Protection-implementatiefouten, aantal foutcodes voor Endpoint Protection-beleid  

   - Endpoint Protection tegen schadelijke software en het gebruik van Windows Firewall-beleid (aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Deze gegevens bevatten niet geen informatie over de instellingen die zijn opgenomen in het beleid.  


### <a name="migration"></a>Migratie  

  - Aantal gemigreerde objecten (gebruik van de migratiewizard)


### <a name="mobile-device-management-mdm"></a>Beheer van mobiele apparaten (MDM)  

   - Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode rest, wissen, buiten gebruik stellen en nu opdrachten synchroniseren

   - Aantal beleidsregels voor mobiele apparaten  

   - Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn geregistreerd (massaal, op basis van gebruikers)  

   - Telling van gebruikers met meerdere ingeschreven mobiele apparaten  

   - Mobiele apparaten polling-planning en statistieken voor de duur van inchecken mobiele apparaten  


### <a name="microsoft-intune-troubleshooting"></a>Probleemoplossing voor Microsoft Intune  

   - Aantal en grootte van apparaatacties (wissen, buiten gebruik stellen, vergrendelen), Telemetrie en gegevensberichten die zijn gerepliceerd naar Microsoft Intune

   - Aantal en grootte van status, status, inventaris, RDR, DDR, UDX, Tenant staat, POL, LOG, Cert, CRP, Resync, CFD, RDO, BEX, ISM en naleving berichten die worden gedownload van Microsoft Intune

   - Volledige statistieken en deltastatistieken over Gebruikerssynchronisatie voor Microsoft Intune


### <a name="on-premises-mobile-device-management-mdm"></a>On-premises Mobile Device Management (MDM)  

   - Aantal Windows 10-bulkregistratiepakketten en -profielen  

   - Statistieken over geslaagde/mislukte lokale MDM-toepassingsimplementaties  


### <a name="os-deployment"></a>Implementatie van het besturingssysteem  

   - Aantal opstartinstallatiekopieën, stuurprogramma's, stuurprogrammapakketten, distributiepunten met ingeschakelde multicast, distributiepunten voor PXE-functionaliteit en takenreeksen  

   - Aantal opstartinstallatiekopieën door Configuration Manager-clientversie

   - Telling van opstartinstallatiekopieën met Windows PE-versie

   - Telling van de editie-Upgradebeleid

   - Het aantal hardware-id's die zijn uitgesloten van PXE

   - Telling van het besturingssysteem-implementatie door de versie van besturingssysteem

   - Telling van het besturingssysteem upgrades gedurende een periode

   - Telling van implementaties van takenreeksen met de optie voor het vooraf downloaden van inhoud

   - Telt het aantal van de taak sequence stap gebruik

   - Versie van Windows ADK is geïnstalleerd


### <a name="site-updates"></a>Site is bijgewerkt  

   - Versies van geïnstalleerde hotfixes voor Configuration Manager


### <a name="software-updates"></a>Software-updates  

   - Beschikbaar- en deadlinedelta's die worden gebruikt in regels voor automatische implementatie  

   - Gemiddeld en maximumaantal toewijzingen per update  

   - Evaluatie van client-updates en scanplanningen  

   - Classificaties die worden gesynchroniseerd met de software-updatepunt

   - Statistieken over clusterpatching  

   - Configuratie van Windows 10 express-updates

   - Configuraties die worden gebruikt voor actieve Windows 10-onderhoudsplannen  

   - Aantal geïmplementeerde Office 365-updates  

   - Aantal van de Microsoft Surface stuurprogramma's die zijn gesynchroniseerd

   - Aantal updategroepen en toewijzingen  

   - Aantal updatepakketten en de minimale/maximale/gemiddelde aantal distributiepunten die zijn gericht aan pakketten  

   - Telling van updates die zijn gemaakt en geïmplementeerd met System Center Update Publisher  

   - Telling van Windows Update voor bedrijven-beleid gemaakt en geïmplementeerd

   - ***[Nieuw]***  Geaggregeerd statistieken van Windows Update voor bedrijven-configuraties

   - Aantal regels voor automatische implementatie die zijn gekoppeld aan synchronisatie  

   - Aantal regels voor automatische implementatie waarmee nieuwe updates worden gemaakt of waarmee updates worden toegevoegd aan een bestaande groep  

   - Aantal regels voor automatische implementatie met meerdere implementaties  

   - Aantal updategroepen en minimaal/maximaal/gemiddeld aantal updates per groep  

   - Aantal updates en het percentage van de updates die zijn geïmplementeerd, verlopen, vervangen, gedownload en bevatten of een gebruiksrechtovereenkomst  

   - Software-update-punt voor de load balancer statistieken

   - Synchronisatieplanning voor software-updatepunten  

   - Totaalaantal/gemiddeld aantal verzamelingen met software-update-implementaties en het maximale/gemiddelde aantal geïmplementeerde updates  

   - Foutcodes voor updatescans en het aantal computers  

   - Versies van Windows 10-dashboardinhoud  


### <a name="sqlperformance-data"></a>SQL/prestatiegegevens  

   - Configuratie en de duur van de samenvatting van de site

   - Aantal van de grootste databasetabellen  

   - Operationele statistieken over gebruikersdetectie (aantal objecten gevonden)

   - Detectie-typen, ingeschakeld en plannen (volledige, incrementele)

   - SQL AlwaysOn-replica informatie, informatie over het gebruik en health-status

   - SQL bijhouden prestatieproblemen bewaarperiode en status automatisch opschonen

   - Bewaarperiode voor bijhouden van SQL

   - Toestand en status bericht prestatiestatistieken met inbegrip van de meest voorkomende en meest duur berichttypen


### <a name="miscellaneous"></a>Diverse  

   - Configuratie van datawarehouse-servicepunt inclusief synchronisatie schema en de gemiddelde tijd

   - Telling van scripts en uitvoeren statistieken

   - Aantal sites met Wake op LAN (WOL)

   - Gebruik en prestaties rapportages
  
   - ***[Nieuw]***  Gefaseerde implementatie gebruiksstatistieken



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau volledig omvat alle gegevens in de niveaus basis en uitgebreid. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates. Dit niveau kan ook geavanceerde diagnostische gegevens, zoals systeembestanden en momentopnamen van het geheugen, die mogelijk persoonlijke gegevens bevatten die in het geheugen of logboekbestanden op het moment van vastleggen voorkomen bevatten.

Voor Configuration Manager versie 1802 omvat dit niveau de volgende gegevens:

- Informatie over de evaluatieplanning voor regels voor automatische implementatie

- Samenvatting van status ATP

- Evaluatie van verzamelingen en vernieuwingsstatistieken

- Beleid nalevingsstatistieken op naleving en fouten

- Instellingen voor naleving: Beleid sjabloon configuratiedetails SCEP, VPN, Wi-Fi en naleving

- DCM-config pack voor het gebruik van System Center Configuration Manager

- Gedetailleerde client implementatie installatiefouten

- Overzicht Endpoint Protection-status: waaronder het aantal beveiligde, risicoclients, onbekende en niet-ondersteunde clients

- Endpoint Protection-beleidsconfiguratie

- Lijst met processen die zijn geconfigureerd met installatiegedrag voor toepassingen

- Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

- Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

- Minimaal/maximaal/gemiddeld aantal software-updates per pakket

- ***[Bijgewerkt]***  MSI product code implementatiestatistieken 

- Algemene naleving van software-update-implementaties

- Telling van groepen die zijn verlopen software-updates

- Aantal fouten en foutcodes voor software-update-implementaties

- Informatie over de implementatie van de software-update: percentage van implementaties die zijn gericht met client versus UTC-tijd, vereist optioneel versus stil en opnieuw opstarten onderdrukken

- Software-update-producten gesynchroniseerd door software-updatepunt

- Percentage van geslaagde software-updatescans

- Top 50 CPU's in de omgeving

- Type van Exchange Active Sync (EAS) beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die door Microsoft Intune beheert

- Microsoft Store voor bedrijven toepassingsgegevens: niet-samengestelde lijst van gesynchroniseerde toepassingen, waaronder AppID, online is of offlinestatus en totaal aantal aangeschafte licentieaantallen
