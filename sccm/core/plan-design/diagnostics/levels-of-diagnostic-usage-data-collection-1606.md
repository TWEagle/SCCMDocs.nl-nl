---
title: Diagnostische gegevens voor 1606 | Microsoft Docs
description: Meer informatie over de niveaus van diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager versie 1606 worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7350d03-f440-4744-82d4-75f8c6c25028
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
ms.openlocfilehash: 27eb4225b7e907772fa5ed8b209fc04fa9f3a677
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1606-of-system-center-configuration-manager"></a>Niveaus van diagnostische gebruiksgegevens verzamelen van gegevens voor versie 1606 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1606 verzamelt drie niveaus van diagnostische gegevens en gebruiksgegevens: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bieden aanvullende details over de gegevens die elk niveau worden verzameld.

Wijzigingen van vorige versies worden vermeld met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager verzamelt geen sitecodes, namen van sites, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op het niveau basis of uitgebreid. Een verzameling van deze informatie op het niveau volledig is niet doelgericht, dat wil zeggen, mogelijk opgenomen in de geavanceerde diagnostische gegevens, zoals logboekbestanden of momentopnamen van het geheugen. Microsoft gebruikt deze gegevens niet voor u te identificeren, contact met u of reclame ontwikkelen.

##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders met een op rollen gebaseerd administratief bereik dat omvat **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen voor diagnostische gegevens en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

   Hiertoe klikt u in de console, Ga naar het backstage-tabblad (de tab linksboven met de vervolgkeuzepijl), selecteer **gebruiksgegevens**, en selecteer vervolgens het niveau van de gegevens die u wilt gebruiken.  

##  <a name="bkmk_level1"></a> Niveau 1 - Basis
 Het niveau basis omvat gegevens over uw hiërarchie, de gegevens die vereist zijn om u te helpen verbeteren van de installatie of upgrade-ervaring en gegevens die u helpt te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

 U begint met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:


 -   Installatie-informatie:
      - Bouwen, installeert u type, taalpakketten, functies die u hebt ingeschakeld  

      -   Update pack Implementatiestatus en fouten, downloaden de voortgang en fouten in de vereisten  

      -  Versie van na de upgrade-script

      -  Gebruik van de update snelle-ring

-   Databaseprestatiegegevens (replicatie verwerken van gegevens, bovenste procedures voor het SQL Server opgeslagen door de processor en het schijfgebruik)

-   Elementaire databaseconfiguratie (processors, clusterconfiguratie en configuratie van gedistribueerde weergaven)

-   Configuration Manager-databaseschema (hash van alle objectdefinities)

-   Telling van Configuration Manager-clientversies en besturingssysteemversies

-   Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

-   Aantal clienttalen en landinstellingen

-   Aantal Windows 10-apparaten per branch en build

-   Configuration Manager site hiërarchie basisgegevens (sitelijst, type, versie, status, aantal clients en tijdzone)

-   Basic serverinformatie sitesysteem (gebruikte sitesysteemrollen, Internet- en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

-   Elementaire statistieken over gebruikersdetectie (gebruiker detectie telling en het minimale/maximale/gemiddelde groepsgrootten)

-   Basisinformatie van Endpoint Protection (antimalwareclients)

-   Het type standaard toepassing en implementatietype telt (totaalaantal apps, totaalaantal apps met meerdere implementatietypen, totaalaantal apps met afhankelijkheden, totaalaantal vervangen apps en het aantal implementatietechnologieën dat in gebruik)

-   Basic-besturingssysteem-implementatie (OSD) telt (installatiekopieën)

-   Distributiepunt- en beheerpunttypen en basisinformatie over de configuratie (beveiligd, voorbereid, PXE, multicast, SSL-status, pull/peer-distributiepunten, MDM-functionaliteit, SSL is ingeschakeld, enz.)

-   Telemetriestatistieken (wanneer uitgevoerd, runtime en fouten)

-  Geconfigureerde telemetrie niveau, modus (online of offline) en snelle update-configuratie

-  Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)
-  Beheerconsole:

     -  Statistieken over consoleverbindingen (besturingssysteemversie, taal, SKU en architectuur, het systeemgeheugen aantal logische processors, site-ID, de geïnstalleerde versies van .NET en taalpakketten console verbinden)    


- ***[Nieuw] *** SQL versie, servicepackniveau edition, sorterings-ID en -teken instellen


##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau uitgebreid is de standaardinstelling nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het niveau basis, onderdeelspecifieke gegevens (frequentie en duur van gebruik), Configuration Manager-clientinstellingen (onderdeelnaam, status en bepaalde instellingen zoals polling-intervallen) en basisgegevens over software-updates.

Dit niveau wordt aanbevolen omdat u Microsoft de minimumhoeveelheid gegevens die vereist zijn biedt om nuttige verbeteringen in toekomstige versies van producten en services. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), details over beveiliging gerelateerde objecten of over beveiligingsproblemen zoals het aantal systemen waarvoor software-updates.

U begint met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:

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

    - ***[Nieuw] *** Telling van Windows Store voor bedrijven-apps en sync-statistieken (inclusief samengevatte typen apps)  

    - ***[Nieuw] *** Grens beheergroep statistieken (hoeveel snel, hoeveel vertragen en count per groep)

    - ***[Nieuw] *** MSI-configuratie-opties en telt

    - ***[Nieuw] *** Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

    - ***[Nieuw] *** Vervanging van de app, de maximale diepte van een keten van

    - ***[Nieuw] *** Gebruik universal Data Access (UDA) en hoe zijn gemaakt



-   **Client:**  

    -   Lijst met en aantal ingeschakelde clientagents  

    -   Aantal clientinstallaties vanaf elk bronlocatietype  

    -   Aantal mislukte clientinstallaties  

    -  ***[Nieuw] *** Automatische upgrade-implementatie voor clientconfiguratie, inclusief clientproef

    -  ***[Nieuw] *** Client health statistieken en samenvatting van het bovenste probleem

    - ***[Nieuw] *** BIOS leeftijd in jaren

    - ***[Nieuw] *** Besturingssysteem leeftijd in maanden

    - ***[Nieuw] *** Telling van Software Center-acties

    - ***[Nieuw] *** Clientversie active Management Technology (AMT)

    - ***[Nieuw] *** Client downloaden implementatiefouten

    - ***[Nieuw] *** Melding bewerking actie clientstatus (het aantal keren is uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)

    - ***[Nieuw] *** Implementatiemethoden gebruikt voor de client en de telling van clients per methode-implementatie

    - ***[Nieuw] *** Grootte van de clientconfiguratie-cache



- ***[Nieuw] *** **Cloudservices:**

  - ***[Nieuw] *** Aantal verzamelingen die zijn gesynchroniseerd met Operations Management Suite

  - ***[Nieuw] *** Cloudconnector of de Operations Management Suite is ingeschakeld



- ***[Nieuw] Verzamelingen:***

    -  ***[Verplaatst] *** Verzameling evaluatie-statistieken (query tijd, toegewezen en niet-toegewezen aantallen geteld met type, de overschakeling van de ID en het gebruik van de regel)

    - ***[Nieuw] *** Verzamelingen zonder een implementatie

    - ***[Nieuw] *** Verzamelings-ID-syntaxis (wordt niet uitgevoerd buiten de id's)



-   **Compatibiliteitsinstellingen:**  

    -   Aantal configuratie-items per type  

    -   Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    -   ***[Bijgewerkt] *** Aantal implementaties die verwijzen naar ingebouwde instellingen (nu vastleggen instelling herstellen)  

    -   ***[Bijgewerkt] *** Aantal regels en implementaties die zijn gemaakt voor aangepaste instellingen (nu vastleggen instelling herstellen)  
    -   Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP), VPN, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    -  Telling van SCEP-certificaat, VPN, Wi-Fi, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - ***[Nieuw] *** Passport for Work-beleid (gemaakt, geïmplementeerd)



-   **Inhoud:**  

    -   Aantal grenzen per type  

    -   Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    -   Informatie over punt distributie (aantal pakketten en distributiepunten die zijn toegewezen aan elke distributiepuntengroep)  

    -   Distribution point configuratiegegevens (gebruik van vertakkingscache en bewaking van distribution point)  

    -   Distribution Manager configuratie-informatie (threads, vertraging, aantal nieuwe pogingen, en pull-distributiepuntinstellingen)  


-   **Endpoint Protection:**  

    -   Endpoint Protection tegen schadelijke software en het gebruik van Windows Firewall-beleid (aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit omvat geen informatie over de instellingen die zijn opgenomen in het beleid.  

    -   Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid)  

    -   Aantal verzamelingen die zijn geselecteerd worden weergegeven in het dashboard Endpoint Protection  

    -   Aantal waarschuwingen die zijn geconfigureerd voor de functie Endpoint Protection  

    - ***[Nieuw] *** Advanced Threat Protection (ATP)-beleid (aantal beleidsregels en of het beleid wordt geïmplementeerd)


-   ***[Verwijderd] *** **Mobile application management (MAM):**  

    -   ***[Verwijderd] *** Aantal MAM geschikte Office-toepassingen, line-of-business-toepassingen en -beleid door het besturingssysteem  

    -   ***[Verwijderd] *** Aantal MAM-toepassings/beleidsimplementaties  

    -   ***[Verwijderd] *** Aantal regels dat per MAM-instelling worden gemaakt  


- ***[Nieuw] *** **Migratie:**

  -  ***[Nieuw] *** Aantal gemigreerde objecten (gebruik van de migratiewizard)



-   **Mobile Device Management (MDM):**  

    -   Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode plaatst, wissen en buiten gebruik stellen opdrachten  

    -   Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn geregistreerd (massaal of op basis van gebruikers)  

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

    -   ***[Nieuw] *** Tellingen van takenreeks stap gebruik



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

    -   ***[Nieuw] *** Software-update-punt voor de load balancer statistieken



-   **SQL/prestatiegegevens:**  

    -   Aantal van de grootste databasetabellen  

    -   Informatie over SQL Always-On-replica  

    -  Bewaarperiode voor bijhouden van SQL

    - ***[Nieuw] *** Detectie typen, ingeschakeld en planning (volledig, incrementele)

    - ***[Nieuw] *** Operationele statistieken over gebruikersdetectie (aantal objecten gevonden)

    - ***[Nieuw] *** SQL bijhouden prestatieproblemen bewaarperiode en status automatisch opschonen



- ***[Nieuw] *** **Diverse**

    - ***[Nieuw] *** Aantal sites met Wake op Lan (WOL)



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau volledig omvat alle gegevens in de niveaus basis en uitgebreid. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates. Dit niveau kan ook geavanceerde diagnostische gegevens, zoals systeembestanden en momentopnamen van het geheugen die mogelijk persoonlijke gegevens bevatten die in het geheugen of logboekbestanden op het moment van vastleggen voorkomen bevatten.

U begint met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:

-   Evaluatie van verzamelingen en vernieuwingsstatistieken

-   Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

-   Endpoint Protection-beleidsconfiguratie

-   Informatie over de implementatie van de software-update (percentage van implementaties die zijn gericht met client versus UTC-tijd, vereist optioneel versus stil en opnieuw opstarten onderdrukken)

-   Algemene naleving van software-update-implementaties

-   Informatie over de evaluatieplanning voor regels voor automatische implementatie

-   ***[VERWIJDERD] *** Aantal clients dat beveiliging netwerktoegangsbeleid hebben

-   Aantal fouten en foutcodes voor software-update-implementaties

-   Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

-   Telling van groepen die zijn verlopen software-updates

-   Minimaal/maximaal/gemiddeld aantal software-updates per pakket

-   Percentage van geslaagde software-updatescans

-   Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

-    Software-update-producten gesynchroniseerd door Software-updatepunt
-    Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid configuratiedetails voor sjabloon

-    Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

-   ***[Nieuw] *** Top 50 CPU's in de omgeving

-   ***[Nieuw] *** DCM config pack voor het gebruik van System Center Configuration Manager

-   ***[Nieuw] *** MSI-productcode (veelgebruikte apps die klanten implementeren)

-   ***[Nieuw] *** ATP Health samenvatting

-   ***[Nieuw] *** Gedetailleerde client implementatie installatiefouten
