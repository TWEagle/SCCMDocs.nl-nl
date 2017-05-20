---
title: On-premises MDM plannen | Microsoft-documenten
description: Plannen voor beheer van mobiele apparaten op locatie voor het beheren van mobiele apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 544c3bea0c7df96887ee1717f061c39c64b82d01
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>On-premises Mobile Device Management plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Overweeg de volgende vereisten voordat het voorbereiden van de Configuration Manager-infrastructuur om af te handelen op\-premises beheer van mobiele apparaten.

##  <a name="bkmk_devices"></a>Ondersteunde apparaten  
 Lokale beheer van mobiele apparaten kunt u mobiele apparaten met behulp van de mogelijkheden voor beheer in de besturingssystemen van apparaten te beheren.  De beheerfunctionaliteit is gebaseerd op de standaard Open Mobile Alliance (OMA) Device Management (DM) en veel apparaatplatformen maken gebruik van deze standaard om het beheer van de apparaten toe te staan.  We bellen deze **moderne apparaten** (in de documentatie en de gebruikersinterface van de Configuration Manager-console) om ze te onderscheiden van andere apparaten waarvoor de Configuration Manager-client te beheren.  

 > [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in beheer van mobiele apparaten On-premises voor apparaten met de volgende besturingssystemen:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(vanaf in Configuration Manager versie 1602\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

##  <a name="bkmk_intune"></a>Gebruik van de Microsoft Intune-abonnement  
 Om te gebruiken op\-premises beheer van mobiele apparaten, moet u een Microsoft Intune-abonnement. Het abonnement is alleen vereist voor het bijhouden van de licentieverlening voor de apparaten en wordt niet gebruikt om de beheergegevens voor de apparaten te beheren of op te slaan. Alle management kan worden opgelost in uw organisatie bedrijf met behulp van de lokale Configuration Manager-infrastructuur.  

 > [!NOTE]  
 > Vanaf versie 1610, Configuration Manager biedt ondersteuning voor beheren van mobiele apparaten met behulp van Microsoft Intune en Configuration Manager-infrastructuur op locatie.   

 Als uw site apparaten met internetverbinding heeft heeft, kan de Intune-service worden gebruikt om te melden om te controleren op het apparaat beheerpunt voor beleidsupdates apparaten. Deze gebruik van Intune is uitsluitend voor melding van de apparaten met internetverbinding. Apparaten zonder internet-verbindingen (en contact kan krijgen met Intune) zijn afhankelijk van het geconfigureerde polling-interval om te controleren met de sitesysteemrollen voor beheerfuncties.  

> [!TIP]  
>  Het is raadzaam dat u de Intune instellen voordat u de vereiste sitesysteemrollen instellen om te voorkomen dat de tijd die nodig is voor de sitesysteemrollen worden functioneel.  

 Zie voor meer informatie over het instellen van de Intune-abonnement [een abonnement op Microsoft Intune instellen voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md).  

##  <a name="bkmk_roles"></a>Vereiste sitesysteemrollen  
 Op\-lokale beheer van mobiele apparaten vereist ten minste één van elk van de volgende sitesysteemrollen:  

-   **Proxypunt voor inschrijving** voor de ondersteuning van inschrijvingsaanvragen.  

-   **Inschrijvingspunt** voor de ondersteuning van apparaatinschrijving.  

-   **Apparaatbeheerpunt** voor de levering van het beleid. Deze sitesysteemrol is een variatie op de beheerpuntrol die is geconfigureerd om het beheer van mobiele apparaten toe te staan.  

-   **Distributiepunt** voor de levering van inhoud.  

-   **Serviceverbindingspunt** voor het verbinden met Intune om in te stellen van apparaten buiten de firewall.  

 Deze sitesysteemrollen kunnen worden geïnstalleerd op de systeemserver van één site of kunnen afzonderlijk worden uitgevoerd op verschillende servers, afhankelijk van de behoeften van uw organisatie. Elke sitesysteemserver gebruikt voor op\-lokale beheer van mobiele apparaten moeten worden geconfigureerd als een HTTPS-eindpunt voor communicatie met de vertrouwde apparaten. Zie [Vereiste vertrouwde communicatie](#bkmk_trustedComs) voor meer informatie.  

 Zie [Plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md) voor meer informatie over het plannen van sitesysteemrollen.  

 Zie [Sitesysteemrollen installeren voor on-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md) voor meer informatie over het toevoegen van de vereiste sitesysteemrollen.  

##  <a name="bkmk_trustedComs"></a>Vertrouwde communicatie vereist  
 Op\-lokale beheer van mobiele apparaten vereist sitesysteemrollen kan worden ingeschakeld voor HTTPS-communicatie. Afhankelijk van uw behoeften kunt u gebruikmaken van de certificeringsinstantie (CA) voor uw onderneming om vertrouwde verbindingen tussen servers en apparaten tot stand te brengen. U kunt ook gebruikmaken van een openbaar toegankelijke certificeringsinstantie als de vertrouwde instantie.  In beide gevallen moet u over een webservercertificaat beschikken die met IIS is geconfigureerd op de sitesysteemservers die als host fungeren voor de vereiste sitesysteemrollen. Daarnaast moet het basiscertificaat van die certificeringsinstantie zijn geïnstalleerd op de apparaten die verbinding moeten maken met die servers.  

 Als u gebruikmaakt van de certificeringsinstantie voor uw onderneming om vertrouwde verbindingen tot stand te brengen, moet u de volgende taken uitvoeren:  

-   Het sjabloon voor het webservercertificaat maken en uitgeven.  

-   Een webservercertificaat aanvragen voor elke sitesysteemserver die als host fungeert voor een vereiste sitesysteemrol.  

-   IIS configureren op de sitesysteemserver zodat het aangevraagde webservercertificaat wordt gebruikt.  

 Voor apparaten die zijn gekoppeld aan het Active Directory-domein van de onderneming is het basiscertificaat van de certificeringsinstantie voor de onderneming al beschikbaar op het apparaat voor vertrouwde verbindingen. Dit betekent dat apparaten die lid zijn van een domein (zoals desktopcomputers) automatisch worden vertrouwd voor HTTPS-verbindingen met de sitesysteemservers. Op apparaten die geen lid zijn van het domein (meestal mobiele apparaten) is het vereiste basiscertificaat echter niet geïnstalleerd. Deze apparaten moet het basiscertificaat handmatig worden geïnstalleerd op deze succesvol kunnen communiceren met sitesysteemservers op ondersteunende\-premises beheer van mobiele apparaten.  

 U moet het basiscertificaat van de verlenende certificeringsinstantie exporteren zodat dit kan worden gebruikt door de afzonderlijke apparaten . U kunt het basiscertificaatbestand verkrijgen door dit met behulp van de certificeringsinstantie te exporteren. Een eenvoudigere methode is om met het webservercertificaat dat is uitgegeven door de certificeringsinstantie de hoofdmap uit te pakken en een basiscertificaatbestand te maken.   Het basiscertificaat moet vervolgens aan het apparaat worden geleverd.  Enkele voorbeelden van leveringsmethoden zijn:  

-   Bestandssysteem  

-   E-mailbijlage  

-   Geheugenkaart  

-   Aangesloten apparaat  

-   Opslag in de cloud (zoals OneDrive)  

-   NFC-verbinding (Near Field Communication)  

-   Streepjescodelezer  

-   OOBE- inrichtingspakket (out of box experience)  

 Zie [Certificaten voor vertrouwde communicatie instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) voor meer informatie.  

##  <a name="bkmk_enrollment"></a>Overwegingen voor inschrijving  
 Inschakelen van inschrijving voor apparaten op\-lokale beheer van mobiele apparaten, gebruikers moeten worden verleend machtiging voor het inschrijven en hun apparaten moeten kunnen vertrouwde communicatie met de sitesysteemservers die als host fungeert voor de vereiste sitesysteemrollen.  

 Inschrijving toestemming voor een gebruiker kan worden uitgevoerd bij het instellen van een inschrijvingsprofiel in Configuration Manager-clientinstellingen. U kunt de standaardclientinstellingen gebruiken om het inschrijvingsprofiel naar alle gedetecteerde gebruikers te pushen of u kunt het inschrijvingsprofiel configureren in de aangepaste clientinstellingen en de instellingen naar een of meer gebruikersverzamelingen pushen.  

 Wanneer de gebruikers zijn gemachtigd om de apparaten in te schrijven, kunnen de gebruikers hun eigen apparaten inschrijven. Als de gebruikers hun apparaat willen inschrijven, moet dit beschikken over het basiscertificaat van de certificeringsinstantie (CA) die het webservercertificaat heeft uitgegeven dat wordt gebruikt op de sitesysteemservers die als host fungeren voor de vereiste sitesysteemrollen.  

 U kunt in plaats van de inschrijving door gebruikers ook een pakket voor bulksgewijs inschrijven instellen. Hiermee wordt toegestaan dat het apparaat wordt ingeschreven zonder tussenkomst van de gebruiker. Dit pakket kan aan het apparaat worden geleverd voordat dit is ingericht voor gebruik of nadat het apparaat het OOBE-proces heeft ondergaan.  

 Zie voor meer informatie over het instellen en inschrijven van apparaten:  

-   [Apparaatinschrijving voor On-premises mobiele apparaten beheren in System Center Configuration Manager instellen](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [Apparaten registreren voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  

