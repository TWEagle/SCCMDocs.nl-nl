---
title: Diagnostische gegevens voor 1511
titleSuffix: Configuration Manager
description: Meer informatie over de niveaus van diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager versie 1511 worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e614ae1-47d2-4a93-ba0a-89dc50d1e266
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
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
ms.openlocfilehash: 4d1b9419a71701fdc29b100e5aec880787e54d8f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1511-of-system-center-configuration-manager"></a>Niveaus van diagnostische gebruiksgegevens verzamelen van gegevens voor versie 1511 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager versie 1511 verzamelt drie niveaus van diagnostische gegevens en gebruiksgegevens: **Basic**, **verbeterde**, en **volledige**. Deze functie is standaard ingesteld op het niveau Uitgebreid. De volgende secties bieden aanvullende details over de gegevens die elk niveau worden verzameld.  

> [!IMPORTANT]  
>  Configuration Manager verzamelt geen sitecodes, namen van sites, IP-adressen, gebruikersnamen, computernamen, fysieke adressen of e-mailadressen op het niveau basis of uitgebreid. Een verzameling van deze informatie op het niveau volledig is niet doelgericht, dat wil zeggen, mogelijk opgenomen in de geavanceerde diagnostische gegevens, zoals logboekbestanden of momentopnamen van het geheugen. Microsoft gebruikt deze gegevens niet voor u te identificeren, contact met u of reclame ontwikkelen.  

##  <a name="bkmk_change"></a> Niveau wijzigen  
 Beheerders met een op rollen gebaseerd administratief bereik dat omvat **wijzigen** machtigingen voor de **Site** objectklasse het niveau van de verzamelde gegevens in de instellingen voor diagnostische gegevens en gebruiksgegevens in de Configuration Manager-console kunt wijzigen.

 Hiertoe klikt u in de console, Ga naar het backstage-tabblad (de tab linksboven met de vervolgkeuzepijl), selecteer **gebruiksgegevens**, en selecteer vervolgens het niveau van de gegevens die u wilt gebruiken.  


##  <a name="bkmk_level1"></a> Niveau 1 - Basis  
 Het niveau basis omvat gegevens over uw hiërarchie, de gegevens die vereist zijn om u te helpen verbeteren van de installatie of upgrade-ervaring en gegevens die u helpt te bepalen van de Configuration Manager-updates die van toepassing zijn op uw hiërarchie.  

 U begint met System Center Configuration Manager versie 1511, omvat dit niveau het volgende:  


-   Installatie-informatie
    - Bouwen, installeert u type, taalpakketten en functies die u hebt ingeschakeld

    - Update pack Implementatiestatus en fouten  

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

##  <a name="bkmk_level2"></a> Niveau 2 - Uitgebreid  
Het niveau uitgebreid is de standaardinstelling nadat setup is voltooid. Dit niveau bevat gegevens die worden verzameld in het niveau basis, onderdeelspecifieke gegevens (frequentie en duur van gebruik), Configuration Manager-clientinstellingen (onderdeelnaam, status en bepaalde instellingen zoals polling-intervallen) en basisgegevens over software-updates).  

Dit niveau wordt aanbevolen omdat u Microsoft de minimumhoeveelheid gegevens die vereist zijn biedt om nuttige verbeteringen in toekomstige versies van producten en services. Dit niveau niet verzamelen objectnamen (sites, gebruikers, computers of objecten), details over beveiliging gerelateerde objecten of over beveiligingsproblemen zoals het aantal systemen waarvoor software-updates.  

U begint met System Center Configuration Manager versie 1511, omvat dit niveau het volgende:  

-   **Toepassingsbeheer:**  

    -   Over Basic gebruik/targeting voor implementatietypen die worden gebruikt binnen de organisatie (gebruiker versus apparaat gericht en vereist versus beschikbaar)  

    -   Informatie over de implementatie van de toepassing (installeren/verwijderen, vereist goedkeuring en gebruikersinteractie ingeschakeld/uitgeschakeld)  

    -   Statistieken over beschikbare toepassingsaanvragen  

    -   Aantal pakketten per type  

    -   Aantal van toepassing zijnde toepassingen per besturingssysteem  

    -   Aantal pakket/programma-implementaties  

    -   Aantal App-V-omgevingen en implementatie-eigenschappen  

    -   Aantal toepassingen met een Windows 10-licentie  

    -   Minimaal/maximaal/gemiddeld aantal toepassingsimplementaties per gebruiker/apparaat  

    -   Type onderhoudsvenster en duur  

-   **Client:**  

    -   Lijst met en aantal ingeschakelde clientagents  

    -   Aantal clientinstallaties vanaf elk bronlocatietype  

    -   Aantal mislukte clientinstallaties  

-   **Compatibiliteitsinstellingen:**  

    -   Aantal configuratie-items per type  

    -   Basislijninformatie over basisconfiguratie (aantal, aantal implementaties en aantal verwijzingen)  

    -   Aantal implementaties die verwijzen naar ingebouwde instellingen (waarde van de instelling wordt niet vastgelegd)  

    -   Aantal regels en implementaties die zijn gemaakt voor de aangepaste instellingen  

    -   Aantal geïmplementeerde Simple Certificate Enrollment Protocol-sjablonen  

-   **Inhoud:**  

    -   Aantal grenzen per type  

    -   Informatie over de grensgroep (aantal grenzen en sitesystemen die zijn toegewezen aan elke grensgroep)  

    -   Informatie over punt distributie (aantal pakketten en distributiepunten die zijn toegewezen aan elke distributiepuntengroep)  

    -   Distribution point configuratiegegevens (gebruik van vertakkingscache en bewaking van distribution point)  

    -   Distribution Manager configuratie-informatie (threads, vertraging, aantal nieuwe pogingen, en pull-distributiepuntinstellingen)  

-   **Endpoint Protection:**  

    -   Endpoint Protection tegen schadelijke software en het gebruik van Windows Firewall-beleid (aantal unieke beleidsregels die zijn toegewezen aan de groep)<br /><br />Dit omvat geen informatie over de instellingen die zijn opgenomen in het beleid.  

    -   Endpoint Protection-implementatiefouten (aantal foutcodes voor Endpoint Protection-beleid)  

    -   Aantal verzamelingen die zijn geselecteerd worden weergegeven in het dashboard Endpoint Protection  

    -   Aantal waarschuwingen die zijn geconfigureerd voor de functie Endpoint Protection  

-   **Mobile Application Management (MAM):**  

    -   Aantal MAM geschikte Office-toepassingen, line-of-business-toepassingen en -beleid door het besturingssysteem  

    -   Aantal MAM-toepassings/beleidsimplementaties  

    -   Aantal regels dat per MAM-instelling worden gemaakt  

-   **Mobile Device Management (MDM):**  

    -   Aantal uitgegeven acties voor mobiele apparaten: vergrendelen, pincode plaatst, wissen en buiten gebruik stellen opdrachten

    -   Telling van mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune en hoe ze zijn geregistreerd (massaal of op basis van gebruikers)  

    -   Mobiele apparaten polling-planning en statistieken voor mobiele apparaten duur van inchecken  

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

-   **Software-updates:**  

    -   Totaalaantal/gemiddeld aantal verzamelingen met software-update-implementaties en het maximale/gemiddelde aantal geïmplementeerde updates  

    -   Aantal regels voor automatische implementatie die zijn gekoppeld aan synchronisatie  

    -   Aantal regels voor automatische implementatie waarmee nieuwe updates worden gemaakt of waarmee updates worden toegevoegd aan een bestaande groep  

    -   Beschikbaar- en deadlinedelta's die worden gebruikt in regels voor automatische implementatie  

    -   Gemiddeld en maximumaantal toewijzingen per update  

    -   Aantal updates dat is gemaakt en geïmplementeerd met System Center Update Publisher  

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

-   **SQL/prestatiegegevens:**  

    -   Aantal van de grootste databasetabellen  

    -   Informatie over SQL Always-On-replica  

    -   Aantal verzamelingen per type  

##  <a name="bkmk_level3"></a> Niveau 3 - Volledig  
Het niveau volledig omvat alle gegevens in de niveaus basis en uitgebreid. Het omvat ook aanvullende informatie over Endpoint Protection, percentages van updatenaleving en informatie over software-updates. Dit niveau kan ook geavanceerde diagnostische gegevens, zoals systeembestanden en momentopnamen van het geheugen, die mogelijk persoonlijke gegevens bevatten die in het geheugen of logboekbestanden op het moment van vastleggen voorkomen bevatten.  

U begint met System Center Configuration Manager versie 1511, omvat dit niveau het volgende:  

-   Evaluatie van verzamelingen en vernieuwingsstatistieken  

-   Samenvatting van Endpoint Protection-status (waaronder het aantal beveiligde clients, risicoclients, onbekende clients en niet-ondersteunde clients)  

-   Endpoint Protection-beleidsconfiguratie  

-   Informatie over de implementatie van de software-update (percentage van implementaties die zijn gericht met client versus UTC-tijd, vereist optioneel versus stil en opnieuw opstarten onderdrukken)  

-   Algemene naleving van software-update-implementaties  

-   Informatie over de evaluatieplanning voor regels voor automatische implementatie  

-   Aantal clients dat beveiliging netwerktoegangsbeleid hebben  

-   Aantal fouten en foutcodes voor software-update-implementaties  

-   Minimaal/maximaal/gemiddeld aantal inactieve clients in verzamelingen voor software-update-implementaties  

-   Telling van groepen die zijn verlopen software-updates  

-   Minimaal/maximaal/gemiddeld aantal software-updates per pakket  

-   Percentage van geslaagde software-updatescans  

-   Minimaal/maximaal/gemiddeld aantal uren sinds de vorige software-updatescan  
