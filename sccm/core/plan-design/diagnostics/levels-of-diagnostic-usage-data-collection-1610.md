---
title: Diagnostische gegevens voor 1610 | System Center Configuration Manager
description: Meer informatie over de niveaus van diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager versie 1610 worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb20eb90-bcc0-41de-bfea-638ea470c0dd
caps.latest.revision: "4"
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
ms.openlocfilehash: ba1e53fdc895690bb958c12d59f82a26067ecad3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1610-of-system-center-configuration-manager"></a>Niveaus van diagnostische gebruiksgegevens verzamelen van gegevens voor 1610-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1610 verzamelt drie niveaus van diagnostische gegevens en gebruiksgegevens: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bieden aanvullende details over de gegevens die elk niveau worden verzameld.

Wijzigingen van vorige versies worden vermeld met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager verzamelt geen sitecodes, namen van sites, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op het niveau basis of uitgebreid. Een verzameling van deze informatie op het niveau volledig is niet doelgericht, dat wil zeggen, mogelijk opgenomen in de geavanceerde diagnostische gegevens, zoals logboekbestanden of momentopnamen van het geheugen. Microsoft gebruikt deze gegevens niet voor u te identificeren, contact met u of reclame ontwikkelen.

##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders met een op rollen gebaseerd administratief bereik dat omvat **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen voor diagnostische gegevens en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

Vanaf versie 1610 kunt u het niveau verzameling uit binnen de console wijzigt door te navigeren naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**. Open **hiërarchie-instellingen**, en selecteer vervolgens de niveau van de gegevens die u wilt gebruiken.  

##  <a name="bkmk_level1"></a> Niveau 1 - Basis
 Het niveau basis omvat gegevens over uw hiërarchie, de gegevens die vereist zijn om u te helpen verbeteren van de installatie of upgrade-ervaring en gegevens die u helpt te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

 Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:


-   Installatie-informatie:
      - Bouwen, installeert u type, taalpakketten, functies die u hebt ingeschakeld  

      - Update pack Implementatiestatus en fouten, downloaden de voortgang en fouten in de vereisten    

      - Versie van na de upgrade-script

      - Gebruik van de update snelle-ring

    - ***[Nieuw] *** Pre-release gebruik, installatietype media, vertakking type

    - ***[Nieuw] *** Software Assurance-vervaldatum

- Meetgegevens over databaseprestaties (informatie over replicatieverwerking, beste in SQL Server opgeslagen procedures op processor- en schijfgebruik)

- Elementaire databaseconfiguratie (processors, clusterconfiguratie en configuratie van gedistribueerde weergaven)

- Configuration Manager-databaseschema (hash van alle objectdefinities)

- Telling van Configuration Manager-clientversies en besturingssysteemversies

- Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

- Aantal clienttalen en landinstellingen

- Aantal Windows 10-apparaten per branch en build

- Configuration Manager site hiërarchie basisgegevens (sitelijst, type, versie, status, aantal clients en tijdzone)

- Basic serverinformatie sitesysteem (gebruikte sitesysteemrollen, Internet- en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

- Elementaire statistieken over gebruikersdetectie (gebruiker detectie telling en het minimale/maximale/gemiddelde groepsgrootten)

- Basisinformatie van Endpoint Protection (antimalwareclients)

- Het type standaard toepassing en implementatietype telt (totaalaantal apps, totaalaantal apps met meerdere implementatietypen, totaalaantal apps met afhankelijkheden, totaalaantal vervangen apps en het aantal implementatietechnologieën dat in gebruik)

- Basic-besturingssysteem-implementatie (OSD) telt (installatiekopieën)

- Distributiepunt- en beheerpunttypen en basisinformatie over de configuratie (beveiligd, voorbereid, PXE, multicast, SSL-status, pull/peer-distributiepunten, MDM-functionaliteit, SSL is ingeschakeld, enz.)

- Telemetriestatistieken (wanneer uitgevoerd, runtimefouten)

- Geconfigureerde telemetrie niveau, modus (online of offline) en snelle update-configuratie

- Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)
- Beheerconsole:

     - Statistieken over consoleverbindingen (besturingssysteemversie, taal, SKU en architectuur, het systeemgeheugen aantal logische processors, site-ID, de geïnstalleerde versies van .NET en taalpakketten console verbinden)    

- SQL-versie, servicepackniveau edition, sorterings-ID en tekenset


##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau uitgebreid is de standaardinstelling nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het niveau basis en functiespecifieke gegevens (frequentie en duur van gebruik), Configuration Manager-clientinstellingen (onderdeelnaam, status en bepaalde instellingen zoals polling-intervallen) en basisgegevens over software-updates.

Dit niveau wordt aanbevolen omdat u Microsoft de minimumhoeveelheid gegevens die vereist zijn biedt om nuttige verbeteringen in toekomstige versies van producten en services. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), details van beveiliging gerelateerde objecten of over beveiligingsproblemen zoals het aantal systemen waarvoor software-updates.

Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:

-   **Toepassingsbeheer:**  

    -    Over Basic gebruik/targeting voor implementatietypen die worden gebruikt binnen de organisatie (gebruiker versus apparaat, vereist versus beschikbaar en universele apps)  

    -   Informatie over de implementatie van de toepassing (installeren/verwijderen, vereist goedkeuring, gebruikersinteractie ingeschakeld/uitgeschakeld, afhankelijkheid en vervangingsimplementatie)  

    -   Statistieken over beschikbare toepassingsaanvragen  

    -   Aantal pakketten per type  

    -   Aantal van toepassing zijnde toepassingen per besturingssysteem  

    -   Aantal pakket/programma-implementaties  

    -   Aantal App-V-omgevingen en implementatie-eigenschappen  

    -   Aantal toepassingen met een Windows 10-licentie  

    -   Minimaal/maximaal/gemiddeld aantal toepassingsimplementaties per gebruiker/apparaat gedurende een periode

    -   Type onderhoudsvenster en duur  

    -  Beleid omvang en complexiteit statistieken

    - ***[Bijgewerkt] *** Telling van Windows Store voor bedrijven-apps en sync statistieken (inclusief samengevatte typen apps gelicentieerde app-status en aantal offline en online gelicentieerde apps)  

    - Grens beheergroep statistieken (hoeveel snel, hoeveel vertragen en count per groep)

    - MSI-configuratieopties en aantallen

    - Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

    - App vervanging van de maximale diepte van een keten van

    - Universele Access (UDA) gebruik, hoe gemaakt

    - ***[Nieuw] *** Toepassing goedkeuring statistische gegevens en gebruiksgegevens frequentie



-   **Client:**  

    -   Lijst met en aantal ingeschakelde clientagents  

    -   Aantal clientinstallaties vanaf elk bronlocatietype  

    -   Aantal mislukte clientinstallaties  

    -  ***[Bijgewerkt] *** Automatische Clientupgrade: implementatieconfiguratie, met inbegrip van de client testen en de uitsluiting gebruik (uitgebreide interoperabiliteit client)

    -  Client health statistieken en samenvatting van het bovenste probleem

    - BIOS-leeftijd in jaren

    - Besturingssysteem leeftijd in maanden

    - Telling van Software Center-acties

    - Versie van de client Active Management Technology (AMT)

    - Client-implementatiefouten downloaden

    - Melding bewerking actie clientstatus (het aantal keren is uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)

    - Implementatiemethoden voor client en de telling van clients per implementatiemethode gebruikt

    - Grootte van de clientconfiguratie-cache

    - ***[Nieuw] *** Aantal hardware-inventarisklassen, software-inventaris regels en regels voor het verzamelen




- **Cloudservices:**

  - Aantal verzamelingen die zijn gesynchroniseerd met Operations Management Suite

  -  Hiermee wordt aangegeven of de cloud-connector van Operations Management Suite is ingeschakeld

  - ***[Nieuw] *** Statistieken voor configuratie en gebruik van Cloud Management Gateway

  - ***[Nieuw] *** Telling van de Upgrade Analytics Connectors




- **Verzamelingen:**

    -  Verzameling evaluatie-statistieken (Querytijd toegewezen en niet-toegewezen aantallen aantallen per type, de overschakeling van de ID en het gebruik van de regel)

    - Verzamelingen zonder een implementatie

    - Verzameling-ID-syntaxis (wordt niet uitgevoerd buiten de id's)



-   **Compatibiliteitsinstellingen:**  

    -   Aantal configuratie-items per type  

    -   Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    -   Aantal implementaties die verwijzing naar ingebouwde instellingen (nu vastleggen instelling herstellen)  

    -   Aantal regels en implementaties die zijn gemaakt voor aangepaste instellingen (nu vastleggen instelling herstellen)  
    -   Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP), VPN, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    -  Telling van SCEP-certificaat, VPN, Wi-Fi, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - Passport for Work-beleid (gemaakt, geïmplementeerd)



-   **Inhoud:**  

    -   Aantal grenzen per type  

    -   Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    - ***[Nieuw] *** Groepsrelaties grens en alternatieve configuratie

    -   Informatie over punt distributie (aantal pakketten en distributiepunten die zijn toegewezen aan elke distributiepuntengroep)  

    -   Distribution point configuratiegegevens (gebruik van vertakkingscache en bewaking van distribution point)  

    -   Distribution Manager configuratie-informatie (threads, vertraging, aantal nieuwe pogingen, en pull-distributiepuntinstellingen)  

    - ***[Nieuw] *** Telling van peer-cacheclients en statistieken voor Poortgebruik

    - ***[Nieuw] *** Client downloaden van inhoud statistieken


-   **Endpoint Protection:**  

    -   Endpoint Protection tegen schadelijke software en het gebruik van Windows Firewall-beleid (aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit omvat geen informatie over de instellingen die zijn opgenomen in het beleid.  

    -   Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid)  

    -   Aantal verzamelingen die zijn geselecteerd worden weergegeven in de Endpoint Protection-dashboard  

    -   Aantal waarschuwingen die zijn geconfigureerd voor Endpoint Protection-functie  

    -   Geavanceerde Threat Protection (ATP)-beleid (aantal beleidsregels en of het beleid wordt geïmplementeerd)


- **Migratie:**

  -   Aantal gemigreerde objecten (gebruik van de migratiewizard)



-   **Mobile Device Management (MDM):**  

    -   ***[Bijgewerkt] *** Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode rest, wissen, buiten gebruik stellen en nu opdrachten synchroniseren  

    -   Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn geregistreerd (massaal, op basis van gebruikers)  

    -   Mobiele apparaten polling-planning en statistieken voor de duur van inchecken mobiele apparaten  

    -   Aantal beleidsregels voor mobiele apparaten  

    -   Telling van gebruikers met meerdere ingeschreven mobiele apparaten  

-   **Microsoft Intune voor probleemoplossing:**

    -   Aantal en grootte van status, status, inventaris, RDR, DDR, UDX, Tenant staat, POL, LOG, Cert, CRP, Resync, CFD, RDO, BEX, ISM en naleving berichten die worden gedownload van Microsoft Intune

    -   Aantal en grootte van apparaatacties (wissen, buiten gebruik stellen, vergrendelen), Telemetrie en gegevensberichten die zijn gerepliceerd naar Microsoft Intune

    -   Volledige statistieken en deltastatistieken over Gebruikerssynchronisatie voor Microsoft Intune


-   **Lokaal Mobile Device Management (MDM)**  

    -   Statistieken over geslaagde/mislukte lokale MDM-toepassingsimplementaties  

    -   Aantal Windows 10-bulkregistratiepakketten en -profielen  



-   **Implementatie van besturingssysteem:**  

    -   Aantal opstartinstallatiekopieën, stuurprogramma's, stuurprogrammapakketten, distributiepunten met ingeschakelde multicast, distributiepunten voor PXE-functionaliteit en takenreeksen  

    -   Telt het aantal van de taak sequence stap gebruik

    - ***[Nieuw] *** Telling van de editie-Upgradebeleid



-   **Site is bijgewerkt:**

    - Versies van geïnstalleerde hotfixes voor Configuration Manager




-   **Software-updates:**  

    -   Totaalaantal/gemiddeld aantal verzamelingen met software-update-implementaties en het maximale/gemiddelde aantal geïmplementeerde updates  

    -   Aantal regels voor automatische implementatie die zijn gekoppeld aan synchronisatie  

    -   Aantal regels voor automatische implementatie waarmee nieuwe updates worden gemaakt of waarmee updates worden toegevoegd aan een bestaande groep  

    -   Beschikbaar- en deadlinedelta's die worden gebruikt in regels voor automatische implementatie  

    -   Gemiddeld en maximumaantal toewijzingen per update  

    -   Telling van updates die zijn gemaakt en geïmplementeerd met System Center Update Publisher  

    -   Aantal updategroepen en toewijzingen  

    -   Aantal updatepakketten en de minimale/maximale/gemiddelde aantal distributiepunten die zijn gericht aan pakketten  

    -   Aantal updategroepen en minimaal/maximaal/gemiddeld aantal updates per groep  

    -   Aantal updates en het percentage van de updates die zijn geïmplementeerd, verlopen, vervangen, gedownload en bevatten of een gebruiksrechtovereenkomst  

    -   Foutcodes voor updatescans en het aantal computers  

    -   Evaluatie van client-updates en scanplanningen  

    -   Synchronisatieplanning voor software-updatepunten  

    -   Aantal regels voor automatische implementatie met meerdere implementaties  

    -   Configuraties die worden gebruikt voor actieve Windows 10-onderhoudsplannen  

    -   Versies van Windows 10-dashboardinhoud  

    -   Aantal Windows 10-clients die gebruikmaken van Windows Update voor bedrijven  

    -   Statistieken over clusterpatching  

    -   Aantal geïmplementeerde Office 365-updates  

    -   Classificaties die worden gesynchroniseerd met de Software-updatepunt

    -   Software-update-punt voor de load balancer statistieken

    -  ***[Nieuw] *** Configuratie van Windows 10 express updates




-   **SQL/prestatiegegevens:**  

    -   Aantal van de grootste databasetabellen  

    -   ***[Bijgewerkt] *** SQL AlwaysOn-replica informatie, informatie over het gebruik en health-status

    -  Bewaarperiode voor bijhouden van SQL

    - Detectie-typen, ingeschakeld en planning (volledig, incrementele)

    - Operationele statistieken over gebruikersdetectie (aantal objecten gevonden)

    - SQL bijhouden prestatieproblemen bewaarperiode en status automatisch opschonen



- **Diverse**

    - Aantal sites met Wake op Lan (WOL)

    - ***[Nieuw] *** Reporting statistieken over gebruik en prestaties  



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau volledig omvat alle gegevens in de niveaus basis en uitgebreid. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates.  Dit niveau kan ook geavanceerde diagnostische gegevens, zoals systeembestanden en momentopnamen van het geheugen die mogelijk persoonlijke gegevens bevatten die in het geheugen of logboekbestanden op het moment van vastleggen voorkomen bevatten.

Voor System Center Configuration Manager versie 1610, dit niveau omvat het volgende:

-   Evaluatie van verzamelingen en vernieuwingsstatistieken

-   Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

-   Endpoint Protection-beleidsconfiguratie

-   Informatie over de implementatie van de software-update (percentage van implementaties die zijn gericht met client versus UTC-tijd, vereist optioneel versus stil en opnieuw opstarten onderdrukken)

-   Algemene naleving van software-update-implementaties

-   Informatie over de evaluatieplanning voor regels voor automatische implementatie

-   Aantal fouten en foutcodes voor software-update-implementaties

-   Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

-   Telling van groepen die zijn verlopen software-updates

-   Minimaal/maximaal/gemiddeld aantal software-updates per pakket

-   Percentage van geslaagde software-updatescans

-   Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

-    Software-update-producten gesynchroniseerd door Software-updatepunt
-    Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid configuratiedetails voor sjabloon

-    Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

-   Top 50 CPU's in de omgeving

-   DCM-config pack voor het gebruik van System Center Configuration Manager

-   MSI-productcode (veelgebruikte apps die klanten implementeren)

-   Samenvatting van status ATP

-   Gedetailleerde client implementatie installatiefouten

- ***[Nieuw] *** Windows Store voor bedrijven toepassingsgegevens (niet-samengestelde lijst met gesynchroniseerde toepassingen, waaronder AppID, online is of offlinestatus en totaal aantal aangeschafte licentieaantallen)
