---
title: Diagnostische gegevens voor 1702
titleSuffix: Configuration Manager
description: Meer informatie over de niveaus van diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager versie 1702 worden verzameld.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d43ab033-2902-4681-8716-b4b17a6df372
caps.latest.revision: "4"
author: aaroncz
ms.author: aaroncz
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
ms.openlocfilehash: 36c50281f0c0188da8e7c24b281881357e4f781c
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1702-of-system-center-configuration-manager"></a>Niveaus van diagnostische gebruiksgegevens verzamelen van gegevens voor 1702-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1702 verzamelt drie niveaus van diagnostische gegevens en gebruiksgegevens: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bieden aanvullende details over de gegevens die elk niveau worden verzameld.

Wijzigingen van vorige versies worden vermeld met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager verzamelt geen sitecodes, namen van sites, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op het niveau basis of uitgebreid. Een verzameling van deze informatie op het niveau volledig is niet doelgericht, dat wil zeggen, mogelijk opgenomen in de geavanceerde diagnostische gegevens, zoals logboekbestanden of momentopnamen van het geheugen. Microsoft gebruikt deze gegevens niet voor u te identificeren, contact met u of reclame ontwikkelen.



##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders met een op rollen gebaseerd administratief bereik dat omvat **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen voor diagnostische gegevens en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

U wijzigt het niveau van de gegevens-verzameling van binnen de console door te navigeren naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**. Open **hiërarchie-instellingen**, en selecteer vervolgens de niveau van de gegevens die u wilt gebruiken.  



##  <a name="bkmk_level1"></a> Niveau 1 - Basis
Het niveau basis omvat gegevens over uw hiërarchie, de gegevens die vereist zijn om u te helpen verbeteren van de installatie of upgrade-ervaring en gegevens die u helpt te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- Beheerconsole:
   - Statistieken over consoleverbindingen (besturingssysteemversie, taal, SKU en architectuur, het systeemgeheugen aantal logische processors, site-ID, de geïnstalleerde versies van .NET en taalpakketten console verbinden)

- Het type standaard toepassing en implementatietype telt (totaalaantal apps, totaalaantal apps met meerdere implementatietypen, totaalaantal apps met afhankelijkheden, totaalaantal vervangen apps en het aantal implementatietechnologieën dat in gebruik)

- Configuration Manager site hiërarchie basisgegevens (sitelijst, type, versie, status, aantal clients en tijdzone)

- Elementaire databaseconfiguratie (processors, clusterconfiguratie en configuratie van gedistribueerde weergaven)

- ***[Bijgewerkt]***  Elementaire statistieken over gebruikersdetectie (detectie telling en het minimale/maximale/gemiddelde groepsgrootten) inclusief wanneer de site met de Azure Active Directory-Services wordt uitgevoerd.

- Basisinformatie van Endpoint Protection (antimalwareclients)

- Basic-besturingssysteem-implementatie (OSD) telt (installatiekopieën)

- Basic serverinformatie sitesysteem (gebruikte sitesysteemrollen, Internet- en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

- Configuration Manager-databaseschema (hash van alle objectdefinities)

- Geconfigureerde telemetrie niveau, modus (online of offline) en snelle update-configuratie

- Aantal clienttalen en landinstellingen

- Telling van Configuration Manager-clientversies en besturingssysteemversies

- Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

- Aantal Windows 10-apparaten per branch en build

- Meetgegevens over databaseprestaties (informatie over replicatieverwerking, beste in SQL Server opgeslagen procedures op processor- en schijfgebruik)

- Distributiepunt- en beheerpunttypen en basisinformatie over de configuratie (beveiligd, voorbereid, PXE, multicast, SSL-status, pull/peer-distributiepunten, MDM-functionaliteit, SSL is ingeschakeld, enz.)

- Installatie-informatie:
     - Bouwen, installeert u type, taalpakketten, functies die u hebt ingeschakeld   

     - Gebruik van de voorlopige versie, installatietype media, vertakking type

     - Software Assurance-vervaldatum      

     - Update pack Implementatiestatus en fouten, downloaden de voortgang en fouten in de vereisten     

     - Gebruik van de update snelle-ring

     - Versie van na de upgrade-script

- SQL-versie, servicepackniveau edition, sorterings-ID en tekenset     
- Telemetriestatistieken (wanneer uitgevoerd, runtimefouten)

- Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)




##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau uitgebreid is de standaardinstelling nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het niveau basis en functiespecifieke gegevens (frequentie en duur van gebruik), Configuration Manager-clientinstellingen (onderdeelnaam, status en bepaalde instellingen zoals polling-intervallen) en basisgegevens over software-updates.

Dit niveau wordt aanbevolen omdat u Microsoft de minimumhoeveelheid gegevens die vereist zijn biedt om nuttige verbeteringen in toekomstige versies van producten en services. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), details van beveiliging gerelateerde objecten of over beveiligingsproblemen zoals het aantal systemen waarvoor software-updates.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- **Toepassingsbeheer:**  

   - Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

   - App vervanging van de maximale diepte van een keten van

   - Toepassing goedkeuring statistische gegevens en gebruiksgegevens frequentie

   - ***[Bijgewerkt]***  Informatie over de implementatie van de toepassing (het gebruik van installeren en verwijderen, vereist goedkeuring, gebruikersinteractie ingeschakeld/uitgeschakeld, afhankelijkheid, vervanging en gebruik telling van de functie voor gedrag)  

   - Beleid omvang en complexiteit statistieken

   - Statistieken over beschikbare toepassingsaanvragen

   - ***[Nieuw]***  Basisinformatie over de configuratie voor pakketten en programma's (implementatie-opties en programma-vlaggen)

   - Over Basic gebruik/targeting voor implementatietypen die worden gebruikt binnen de organisatie (gebruiker versus apparaat, vereist versus beschikbaar en universele apps)

   - Grens beheergroep statistieken (hoeveel snel, hoeveel vertragen en count per groep)

   - Aantal App-V-omgevingen en implementatie-eigenschappen

   - Aantal van toepassing zijnde toepassingen per besturingssysteem  

   - ***[Nieuw]***  Telling van de toepassingen waarnaar wordt verwezen door een takenreeks

   - Aantal pakketten per type  

   - Aantal pakket/programma-implementaties  

   - Aantal toepassingen met een Windows 10-licentie  

   - Telling van Windows Store voor bedrijven-apps en sync statistieken (inclusief samengevatte typen apps gelicentieerde app-status en aantal offline en online gelicentieerde apps)  

   - Type onderhoudsvenster en duur  

   - Minimaal/maximaal/gemiddeld aantal toepassingsimplementaties per gebruiker/apparaat gedurende een periode

   - ***[Nieuw]***  Meest gebruikte toepassing foutcodes voor clientinstallatie door implementatietechnologie

   - MSI-configuratieopties en aantallen

   - ***[Nieuw]***  Statistieken over eindgebruikers interactie met de melding voor vereiste software-implementaties   

   - Universele Access (UDA) gebruik, hoe gemaakt




- **Client:**  

   - Versie van de client Active Management Technology (AMT)

   - BIOS-leeftijd in jaren

   - Automatische Clientupgrade: implementatieconfiguratie, met inbegrip van de client testen en de uitsluiting gebruik (uitgebreide interoperabiliteit client)

   - Grootte van de clientconfiguratie-cache

   - Client-implementatiefouten downloaden

   - Client health statistieken en samenvatting van het bovenste probleem

   - Melding bewerking actie clientstatus (het aantal keren is uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)
   - Aantal clientinstallaties vanaf elk bronlocatietype  

   - Aantal mislukte clientinstallaties  

   - ***[Nieuw]***  Telling van apparaten die door Hyper-V- of Azure gevirtualiseerd  

   - Telling van Software Center-acties   

   - ***[Nieuw]***  Telling van UEFI-apparaten

   - Implementatiemethoden voor client en de telling van clients per implementatiemethode gebruikt

   - Lijst met en aantal ingeschakelde clientagents  

   - Besturingssysteem leeftijd in maanden

   - Het aantal hardware-inventarisklassen, software-inventaris regels en regels voor het verzamelen

   - ***[Nieuw]***  Statistieken voor health attestation van apparaten met inbegrip van de meest voorkomende fout codes, aantal van on-premises servers en het aantal apparaten in verschillende statussen.



- **Cloudservices:**

  - Statistieken voor configuratie en gebruik van Cloud Management Gateway

  - ***[Nieuw]***  Telling van clients die zijn gekoppeld aan Azure Active Directory Services

  - Aantal verzamelingen die zijn gesynchroniseerd met Operations Management Suite

  - Telling van de Upgrade Analytics Connectors

  - Hiermee wordt aangegeven of de cloud-connector van Operations Management Suite is ingeschakeld




- **Verzamelingen:**

    - Verzameling-ID-syntaxis (wordt niet uitgevoerd buiten de id's)

    - Verzameling evaluatie-statistieken (Querytijd toegewezen en niet-toegewezen aantallen aantallen per type, de overschakeling van de ID en het gebruik van de regel)

    - Verzamelingen zonder een implementatie




- **Compatibiliteitsinstellingen:**  

    - Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    - Aantal configuratie-items per type  

    - Aantal implementaties die verwijzing naar ingebouwde instellingen (nu vastleggen instelling herstellen)  

    - Aantal regels en implementaties die zijn gemaakt voor aangepaste instellingen (nu vastleggen instelling herstellen)  
    -  Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP), VPN, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    - Telling van SCEP-certificaat, VPN, Wi-Fi, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - Passport for Work-beleid (gemaakt, geïmplementeerd)



- **Inhoud:**  

    - Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    - Groepsrelaties grens en alternatieve configuratie

    - Statistieken voor het downloaden van inhoud van client

    - Aantal grenzen per type  

    - Telling van peer-cacheclients en statistieken voor Poortgebruik

    - Distribution Manager configuratie-informatie (threads, vertraging, aantal nieuwe pogingen, en pull-distributiepuntinstellingen)  

    - Distribution point configuratiegegevens (gebruik van vertakkingscache en bewaking van distribution point)

    - Informatie over punt distributie (aantal pakketten en distributiepunten die zijn toegewezen aan elke distributiepuntengroep)  



- **Endpoint Protection:**  

   - Geavanceerde Threat Protection (ATP)-beleid (aantal beleidsregels en of het beleid wordt geïmplementeerd)

   - Aantal waarschuwingen die zijn geconfigureerd voor Endpoint Protection-functie  

   - Aantal verzamelingen die zijn geselecteerd worden weergegeven in de Endpoint Protection-dashboard  

   - Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid)  

   - Endpoint Protection tegen schadelijke software en het gebruik van Windows Firewall-beleid (aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit omvat geen informatie over de instellingen die zijn opgenomen in het beleid.  



- **Migratie:**

  - Aantal gemigreerde objecten (gebruik van de migratiewizard)



- **Mobile Device Management (MDM):**  

    - Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode rest, wissen, buiten gebruik stellen en nu opdrachten synchroniseren

    - Aantal beleidsregels voor mobiele apparaten  

    - Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn geregistreerd (massaal, op basis van gebruikers)  

    - Telling van gebruikers met meerdere ingeschreven mobiele apparaten  

    - Mobiele apparaten polling-planning en statistieken voor de duur van inchecken mobiele apparaten  




- **Microsoft Intune voor probleemoplossing:**

    - Aantal en grootte van apparaatacties (wissen, buiten gebruik stellen, vergrendelen), Telemetrie en gegevensberichten die zijn gerepliceerd naar Microsoft Intune

    - Aantal en grootte van status, status, inventaris, RDR, DDR, UDX, Tenant staat, POL, LOG, Cert, CRP, Resync, CFD, RDO, BEX, ISM en naleving berichten die worden gedownload van Microsoft Intune

    - Volledige statistieken en deltastatistieken over Gebruikerssynchronisatie voor Microsoft Intune



- **Lokaal Mobile Device Management (MDM)**  

    - Aantal Windows 10-bulkregistratiepakketten en -profielen  

    - Statistieken over geslaagde/mislukte lokale MDM-toepassingsimplementaties  




- **Implementatie van besturingssysteem:**  

    - Aantal opstartinstallatiekopieën, stuurprogramma's, stuurprogrammapakketten, distributiepunten met ingeschakelde multicast, distributiepunten voor PXE-functionaliteit en takenreeksen  

    - Telling van de editie-Upgradebeleid

    - Telt het aantal van de taak sequence stap gebruik



- **Site is bijgewerkt:**

    - Versies van geïnstalleerde hotfixes voor Configuration Manager



- **Software-updates:**  

    - Beschikbaar- en deadlinedelta's die worden gebruikt in regels voor automatische implementatie  

    - Gemiddeld en maximumaantal toewijzingen per update  

    - Evaluatie van client-updates en scanplanningen  

    - Classificaties die worden gesynchroniseerd met de Software-updatepunt

    - Statistieken over clusterpatching  

    - Configuratie van Windows 10 express-updates

    - Configuraties die worden gebruikt voor actieve Windows 10-onderhoudsplannen  

    - Aantal geïmplementeerde Office 365-updates  

    - Aantal updategroepen en toewijzingen  

    - Aantal updatepakketten en de minimale/maximale/gemiddelde aantal distributiepunten die zijn gericht aan pakketten  

    - Telling van updates die zijn gemaakt en geïmplementeerd met System Center Update Publisher  

    - Aantal Windows 10-clients die gebruikmaken van Windows Update voor bedrijven  

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



- **SQL/prestatiegegevens:**  

    - ***[Nieuw]***  Configuratie en de duur van de samenvatting van de site

    - Aantal van de grootste databasetabellen  

    - Operationele statistieken over gebruikersdetectie (aantal objecten gevonden)

    - Detectie-typen, ingeschakeld en planning (volledig, incrementele)

    - SQL AlwaysOn-replica informatie, informatie over het gebruik en health-status

    - SQL bijhouden prestatieproblemen bewaarperiode en status automatisch opschonen

    - Bewaarperiode voor bijhouden van SQL

    - ***[Nieuw]***  Toestand en status bericht prestatiestatistieken, met inbegrip van de meest voorkomende en meest duur berichttypen



- **Diverse**

    - ***[Nieuw]***  Configuratie van datawarehouse Service gegevenspunt met inbegrip van de planning en gemiddelde synchronisatietijd

    - Aantal sites met Wake op Lan (WOL)

    - Gebruik en prestaties rapportages  



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau volledig omvat alle gegevens in de niveaus basis en uitgebreid. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates.  Dit niveau kan ook geavanceerde diagnostische gegevens, zoals systeembestanden en momentopnamen van het geheugen die mogelijk persoonlijke gegevens bevatten die in het geheugen of logboekbestanden op het moment van vastleggen voorkomen bevatten.

Voor System Center Configuration Manager versie 1702, dit niveau omvat het volgende:

- Informatie over de evaluatieplanning voor regels voor automatische implementatie

- Samenvatting van status ATP

- Evaluatie van verzamelingen en vernieuwingsstatistieken

- Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid sjabloon configuratiedetails aantal groepen die zijn verlopen software-updates

- DCM-config pack voor het gebruik van System Center Configuration Manager

- Gedetailleerde client implementatie installatiefouten
- Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

- Endpoint Protection-beleidsconfiguratie

- ***[Nieuw]***  Lijst met processen die zijn geconfigureerd met installatiegedrag voor toepassingen

- Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

- Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

- Minimaal/maximaal/gemiddeld aantal software-updates per pakket

- MSI-productcode (veelgebruikte apps die klanten implementeren)

- Algemene naleving van software-update-implementaties

- Aantal fouten en foutcodes voor software-update-implementaties

- Informatie over de implementatie van de software-update (percentage van implementaties die zijn gericht met client versus UTC-tijd, vereist optioneel versus stil en opnieuw opstarten onderdrukken)

- Software-update-producten gesynchroniseerd door Software-updatepunt

- Percentage van geslaagde software-updatescans

- Top 50 CPU's in de omgeving

- Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

- Windows Store voor bedrijven toepassingsgegevens (niet-samengestelde lijst met gesynchroniseerde toepassingen, waaronder AppID, online is of offlinestatus en totaal aantal aangeschafte licentieaantallen)
