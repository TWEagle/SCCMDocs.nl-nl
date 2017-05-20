---
title: Diagnostische gegevens voor 1606 | Microsoft-documenten
description: Meer informatie over de niveaus van diagnoses en gebruiksgegevens die door System Center Configuration Manager versie 1606 worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7350d03-f440-4744-82d4-75f8c6c25028
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
ms.sourcegitcommit: 688e05aae0e0b15b54835f8d64a98487f4d7b64d
ms.openlocfilehash: 27eb4225b7e907772fa5ed8b209fc04fa9f3a677
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1606-of-system-center-configuration-manager"></a>Niveaus van diagnostische gegevensverzameling gebruiksgegevens voor 1606-versie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1606 worden drie niveaus van diagnostische en gebruiksgegevens worden verzameld: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bevatten meer informatie over gegevens die elk niveau worden verzameld.

Wijzigingen van eerdere versies worden aangegeven met ***[Nieuw]***, ***[bijgewerkt]***, ***[verwijderd]***, of ***[verplaatst]***.


> [!IMPORTANT]
>  Configuration Manager worden niet verzameld sitecodes, sites, namen, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op de basis of uitgebreid niveaus. Een verzameling van deze informatie op het niveau van de volledige is niet purposeful, dat wil zeggen, mogelijk zijn opgenomen in de geavanceerde diagnostische gegevens zoals logboekbestanden of geheugen momentopnamen. Microsoft gebruikt deze gegevens niet geïdentificeerd, contact met u of advertenties ontwikkelen.

##  <a name="bkmk_change"></a> Niveau wijzigen
 Beheerders die een op rollen gebaseerd administratief bereik met **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen diagnostische en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

   Om dit te doen, in de console, Ga naar de backstage tabblad (de bovenste links met de pijl), selecteer **gebruiksgegevens**, en selecteer vervolgens het niveau van de gegevens die u wilt gebruiken.  

##  <a name="bkmk_level1"></a> Niveau 1 - Basis
 De op basisniveau bevat gegevens over uw hiërarchie, de gegevens die vereist zijn om te helpen verbeteren van de installatie of upgrade van de gebruikerservaring en gegevens die u helpen te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.

 Beginnen met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:


 -   Installatie-informatie:
       - Maken, installeert u type, taalpakketten, functies die u hebt ingeschakeld  

       -   Implementatiestatus pack en fouten bijwerken, uitgevoerd en de vereiste fouten downloaden     

       -  Versie van na de upgrade-script

       -  Gebruik van snelle ring update

-   Database maatstaven voor prestaties (replicatie verwerken van gegevens, de beste procedures voor SQL Server opgeslagen door de processor en het schijfgebruik)

-   Basic databaseconfiguratie (processors clusterconfiguratie en configuratie van gedistribueerde weergaven)

-   Schema voor Configuration Manager-database (hash van alle objectdefinities)

-   Telling van Configuration Manager-clientversies en versies van besturingssystemen

-   Telling van besturingssystemen voor beheerde apparaten en beleidsregels die zijn ingesteld door de Exchange-Connector

-   Telling van de clienttalen en landinstellingen

-   Aantal Windows 10-apparaten per branch en build

-   Configuration Manager site hiërarchie basisgegevens (lijst met de site, type, versie, status, aantal clients en tijdzone)

-   Basic server sitesysteeminformatie (sitesysteemrollen gebruikt, via Internet en SSL-status, besturingssysteem, processors, en fysieke of virtuele machine)

-   Basic detectie gebruikersstatistieken (gebruiker detectie aantal of minimum/maximum/gemiddelde groep grootten)

-   Basisinformatie van Endpoint Protection (antimalware-clientversies)

-   Eenvoudige implementatie van toepassingen en -type wordt in mindering gebracht (totaal aantal apps, totale apps met meerdere implementatietypen totale apps met afhankelijkheden totale vervangen apps en telling van implementatietechnologieën in gebruik)

-   Basic besturingssysteemimplementatie (OSD) wordt in mindering gebracht (afbeeldingen)

-   Distributiepunt en beheerpunten typen en basisconfiguratie informatie (beveiligde, voorbereid, PXE, multicast SSL-status pull/peer distributiepunten MDM-functionaliteit, SSL is ingeschakeld, enz.)

-   Statistieken voor telemetrie (wanneer uitgevoerd, runtime en fouten)

-  Geconfigureerde telemetrie niveau, modus (online of offline) en snel update-configuratie

-  Gebruik van netwerkdetectie (ingeschakeld of uitgeschakeld)
-  Beheerconsole:

     -  Statistieken over consoleverbindingen (versie van besturingssysteem, taal, SKU en architectuur, systeemgeheugen, het aantal logische processors, site-ID, geïnstalleerde versies van .NET en taalpakketten console verbinden)    


- ***[Nieuw] *** SQL versie, servicepack-niveau edition, sorterings-ID en -teken instellen


##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid
Het niveau van de verbeterde is de standaard nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het basisniveau, onderdeelspecifieke gegevens (frequentie en duur van gebruik), instellingen voor Configuration Manager-clients (onderdeelnaam, status en bepaalde instellingen zoals pollingintervallen) en algemene informatie over software-updates.

Dit niveau wordt aanbevolen, omdat hiermee het minimumaantal gegevens die vereist zijn nuttig verbeteringen te maken in toekomstige versies van producten en diensten van Microsoft. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computer of objecten), gegevens over objecten productspecifieke beveiliging of problemen zoals tellingen van systemen die software-updates vereisen.

Beginnen met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:

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

    - ***[Nieuw] *** Aantal van de Windows Store voor Business-apps en sync statistieken (inclusief samengevatte typen apps)  

    - ***[Nieuw] *** Grens beheergroep statistieken (hoeveel snel, hoeveel vertragen en tellen per groep)

    - ***[Nieuw] *** MSI-configuratie-opties en wordt in mindering gebracht

    - ***[Nieuw] *** Appvereisten (aantal van ingebouwde voorwaarden wordt verwezen door implementatietechnologie)

    - ***[Nieuw] *** App vervanging, maximale diepte van keten

    - ***[Nieuw] *** Universal Data Access (UDA) gebruik en hoe gemaakt



-   **Client:**  

    -   Lijst met en aantal ingeschakelde clientagents  

    -   Aantal clientinstallaties vanaf elk bronlocatietype  

    -   Aantal mislukte clientinstallaties  

    -  ***[Nieuw] *** Clientconfiguratie voor automatische implementatie client haalbaarheidsonderzoek inclusief

    -  ***[Nieuw] *** Client health statistieken en de belangrijkste probleem samenvatting

    - ***[Nieuw] *** BIOS-ouderdom in jaar

    - ***[Nieuw] *** Besturingssysteem leeftijd in maanden

    - ***[Nieuw] *** Telling van Software Center acties

    - ***[Nieuw] *** Clientversie active Management Technology (AMT)

    - ***[Nieuw] *** Client implementatie downloaden fouten

    - ***[Nieuw] *** Melding opnieuw in te grijpen clientstatus (het aantal keren wordt uitgevoerd, Max. aantal gerichte clients en de gemiddelde Verwerkingsfrequentie)

    - ***[Nieuw] *** Implementatiemethoden gebruikt voor de client en het aantal clients per implementatiemethode

    - ***[Nieuw] *** Clientconfiguratie cache-grootte



- ***[Nieuw] *** **Cloudservices:**

  - ***[Nieuw] *** Aantal verzamelingen die zijn gesynchroniseerd met de Operations Management-pakket

  - ***[Nieuw] *** Cloudconnector of de Operations Management-pakket is ingeschakeld



- ***[Nieuw] Verzamelingen:***

    -  ***[Verplaatst] *** Verzameling evaluatie statistieken (query tijd, toegewezen versus aantal niet-toegewezen, wordt in mindering gebracht op type, de overschakeling van de ID en het gebruik van de regel)

    - ***[Nieuw] *** Verzamelingen zonder een implementatie

    - ***[Nieuw] *** Verzamelings-ID-syntaxis (niet wordt uitgevoerd buiten-id's)



-   **Compatibiliteitsinstellingen:**  

    -   Aantal configuratie-items per type  

    -   Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    -   ***[Bijgewerkt] *** Aantal implementaties die verwijzen naar de standaardinstellingen (nu vastleggen instelling herstellen)  

    -   ***[Bijgewerkt] *** Aantal regels en implementaties die zijn gemaakt voor de aangepaste instellingen (nu vastleggen instelling herstellen)  
    -   Aantal geïmplementeerde sjablonen voor Simple Certificate Enrollment Protocol (SCEP)-, VPN-, Wi-Fi-, certificaat (.pfx) en nalevingsbeleid

    -  Telling van SCEP-certificaat, VPN-, Wi-Fi, certificaat (.pfx) en nalevingsbeleid implementaties per platform

    - ***[Nieuw] *** Passport for Work beleid (gemaakt, geïmplementeerd)



-   **Inhoud:**  

    -   Aantal grenzen per type  

    -   Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    -   Distribution point groepsinformatie (aantal pakketten en distributiepunten die zijn toegewezen aan elk distributiepuntgroep)  

    -   Distribution point configuratiegegevens (gebruik van de vertakking uit cache en distribution point bewaking)  

    -   Distribution Manager configuratiegegevens (threads, tussen elke poging, aantal nieuwe pogingen, en instellingen voor pull-distributiepunten)  


-   **Endpoint Protection:**  

    -   Endpoint Protection schadelijke software en het gebruik van Windows Firewall-beleid (het aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br /> Dit bevat geen informatie over de instellingen die zijn opgenomen in het beleid.  

    -   Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid implementeren)  

    -   Aantal verzamelingen die zijn geselecteerd om te worden weergegeven in het dashboard Endpoint Protection  

    -   Het aantal waarschuwingen die zijn geconfigureerd voor de Endpoint Protection-functie  

    - ***[Nieuw] *** Geavanceerde bedreiging beveiliging (vrije)-beleid (aantal beleidsregels en of beleidsregels worden geïmplementeerd)


-   ***[Verwijderen] *** **Mobile application management (MAM):**  

    -   ***[Verwijderen] *** Telling van MAM ingeschakeld Office-toepassingen, line-of-business-toepassingen en beleid door het besturingssysteem  

    -   ***[Verwijderen] *** Telling van MAM toepassingenbeleid/implementaties  

    -   ***[Verwijderen] *** Aantal regels die zijn gemaakt per MAM-instelling  


- ***[Nieuw] *** **Migratie:**

  -  ***[Nieuw] *** Aantal gemigreerde objecten (gebruik van de migratiewizard)



-   **Mobile Device Management (MDM):**  

    -   Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode plaatst, wissen en buiten gebruik stellen opdrachten  

    -   Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn ingeschreven (bulk of op basis van gebruikers)  

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

    -   ***[Nieuw] *** Tellingen van takenreeks stap gebruik



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

    -   ***[Nieuw] *** Software update-punt load balancing-statistieken



-   **SQL/prestatiegegevens:**  

    -   Aantal van de grootste databasetabellen  

    -   Informatie over SQL Always-On-replica  

    -  Bewaarperiode voor het SQL bijhouden

    - ***[Nieuw] *** Detectie typen, ingeschakeld en planning (volledig, incrementele)

    - ***[Nieuw] *** Detectie operationele statistieken (aantal objecten gevonden)

    - ***[Nieuw] *** SQL bijhouden prestatieproblemen, bewaarperiode of status automatisch opschonen



- ***[Nieuw] *** **Diverse**

    - ***[Nieuw] *** Telling van sites met Wake op Lan (WOL)



##  <a name="bkmk_level3"></a> Niveau 3 - Volledig
Het niveau van de volledige bevat alle gegevens in de Basic en verbeterde niveaus. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates. Dit niveau kan ook geavanceerde diagnostische gegevens zoals systeembestanden en geheugen momentopnamen, waaronder persoonlijke gegevens die beschikbaar in geheugen of logboekbestanden ten tijde van het vastleggen waren.

Beginnen met System Center Configuration Manager versie 1606, omvat dit niveau het volgende:

-   Evaluatie van verzamelingen en vernieuwingsstatistieken

-   Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)

-   Endpoint Protection-beleidsconfiguratie

-   Implementatiegegevens van software-update (percentage van de implementaties die gericht met client ten opzichte van de UTC-tijd vereist optionele ten opzichte van de achtergrond en opnieuw opstarten onderdrukken)

-   Algemene naleving van software-update-implementaties

-   Informatie over de evaluatieplanning voor regels voor automatische implementatie

-   ***[VERWIJDEREN] *** Aantal clients die network access protection beleid

-   Aantal fouten en foutcodes voor software-update-implementaties

-   Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties

-   Telling van groepen die zijn verlopen software-updates

-   Minimaal/maximaal/gemiddeld aantal software-updates per pakket

-   Percentage van geslaagde software-updatescans

-   Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan

-    Software-update producten gesynchroniseerd door Software-updatepunt
-    Instellingen voor naleving: SCEP-, VPN-, Wi-Fi- en nalevingsbeleid configuratiedetails van sjabloon

-    Type EAS beleidsregels voor voorwaardelijke toegang (blokkeren of in quarantaine) voor apparaten die Intune beheert

-   ***[Nieuw] *** Boven 50 CPU's in de omgeving

-   ***[Nieuw] *** DCM config pack voor System Center Configuration Manager-gebruik

-   ***[Nieuw] *** MSI-productcode (algemene apps die klanten implementeren)

-   ***[Nieuw] *** Vrije Health samenvatting

-   ***[Nieuw] *** Gedetailleerde fouten bij de implementatie van client

