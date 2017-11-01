---
title: On-premises MDM plannen
titleSuffix: Configuration Manager
description: Plan voor On-premises Mobile Device Management voor het beheren van mobiele apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: "9"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e1c6a5ccd003295d007e78f0745c30732e10c2df
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="plan-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>On-premises Mobile Device Management plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Overweeg de volgende vereisten voordat het voorbereiden van de Configuration Manager-infrastructuur om af te handelen op\-premises Mobile Device Management.

##  <a name="bkmk_devices"></a>Ondersteunde apparaten  
 Lokaal beheer van mobiele apparaten kunt u mobiele apparaten beheren met de beheermogelijkheden die zijn ingebouwd in de besturingssystemen van apparaten.  De beheerfunctionaliteit is gebaseerd op de standaard Open Mobile Alliance (OMA) Device Management (DM) en veel apparaatplatformen maken gebruik van deze standaard om het beheer van de apparaten toe te staan.  We noemen deze **moderne apparaten** (in de documentatie en de gebruikersinterface van de Configuration Manager-console) ze te onderscheiden van andere apparaten waarvoor de Configuration Manager-client te beheren.  

 > [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in On-premises Mobile Device Management voor apparaten met de volgende besturingssystemen:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(vanaf versie 1602 van Configuration Manager\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

##  <a name="bkmk_intune"></a>Gebruik van de Microsoft Intune-abonnement  
 Om te gebruiken op\-premises Mobile Device Management, moet u een abonnement op Microsoft Intune. Het abonnement is alleen vereist voor het bijhouden van de licentieverlening voor de apparaten en wordt niet gebruikt om de beheergegevens voor de apparaten te beheren of op te slaan. Alle beheer wordt uitgevoerd in uw bedrijfsorganisatie met behulp van de on-premises Configuration Manager-infrastructuur.  

 > [!NOTE]  
 > Vanaf versie 1610, ondersteunt Configuration Manager het beheer van mobiele apparaten met behulp van on-premises infrastructuur voor Configuration Manager en Microsoft Intune.   

 Als uw site apparaten met internetverbinding heeft, kan de Intune-service op de hoogte van apparaten om te controleren op het apparaatbeheerpunt, voor het bijwerken van het beleid wilt worden gebruikt. Dit gebruik van Intune geldt uitsluitend voor meldingen alleen met internet verbonden apparaten. Apparaten zonder internetverbinding (en kan geen verbinding worden gemaakt door Intune) zijn afhankelijk van het geconfigureerde polling-interval om te controleren met de sitesysteemrollen voor beheerfuncties.  

> [!TIP]  
>  Het is raadzaam dat u de Intune instellen voordat u de vereiste sitesysteemrollen instellen om de tijd die nodig zijn voor de sitesysteemrollen functioneel te laten worden.  

 Zie voor informatie over het instellen van het Intune-abonnement, [een Microsoft Intune-abonnement instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md).  

##  <a name="bkmk_roles"></a>Vereiste sitesysteemrollen  
 Op\-premises Mobile Device Management vereist ten minste één van elk van de volgende sitesysteemrollen:  

-   **Proxypunt voor inschrijving** voor de ondersteuning van inschrijvingsaanvragen.  

-   **Inschrijvingspunt** voor de ondersteuning van apparaatinschrijving.  

-   **Apparaatbeheerpunt** voor de levering van het beleid. Deze sitesysteemrol is een variatie op de beheerpuntrol die is geconfigureerd om het beheer van mobiele apparaten toe te staan.  

-   **Distributiepunt** voor de levering van inhoud.  

-   **Serviceaansluitpunt** voor het verbinden met Intune op de hoogte van apparaten buiten de firewall wilt.  

 Deze sitesysteemrollen kunnen worden geïnstalleerd op de systeemserver van één site of kunnen afzonderlijk worden uitgevoerd op verschillende servers, afhankelijk van de behoeften van uw organisatie. Elke sitesysteemserver gebruikt voor op\-premises Mobile Device Management moeten zijn geconfigureerd als een HTTPS-eindpunt voor communicatie met de vertrouwde apparaten. Zie [Vereiste vertrouwde communicatie](#bkmk_trustedComs) voor meer informatie.  

 Zie [Plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md) voor meer informatie over het plannen van sitesysteemrollen.  

 Zie [Sitesysteemrollen installeren voor on-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md) voor meer informatie over het toevoegen van de vereiste sitesysteemrollen.  

##  <a name="bkmk_trustedComs"></a>Vereiste vertrouwde communicatie  
 Op\-premises Mobile Device Management sitesysteemrollen worden ingeschakeld voor HTTPS-communicatie is vereist. Afhankelijk van uw behoeften kunt u gebruikmaken van de certificeringsinstantie (CA) voor uw onderneming om vertrouwde verbindingen tussen servers en apparaten tot stand te brengen. U kunt ook gebruikmaken van een openbaar toegankelijke certificeringsinstantie als de vertrouwde instantie.  In beide gevallen moet u over een webservercertificaat beschikken die met IIS is geconfigureerd op de sitesysteemservers die als host fungeren voor de vereiste sitesysteemrollen. Daarnaast moet het basiscertificaat van die certificeringsinstantie zijn geïnstalleerd op de apparaten die verbinding moeten maken met die servers.  

 Als u gebruikmaakt van de certificeringsinstantie voor uw onderneming om vertrouwde verbindingen tot stand te brengen, moet u de volgende taken uitvoeren:  

-   Het sjabloon voor het webservercertificaat maken en uitgeven.  

-   Een webservercertificaat aanvragen voor elke sitesysteemserver die als host fungeert voor een vereiste sitesysteemrol.  

-   IIS configureren op de sitesysteemserver zodat het aangevraagde webservercertificaat wordt gebruikt.  

 Voor apparaten die zijn gekoppeld aan het Active Directory-domein van de onderneming is het basiscertificaat van de certificeringsinstantie voor de onderneming al beschikbaar op het apparaat voor vertrouwde verbindingen. Dit betekent dat apparaten die lid zijn van een domein (zoals desktopcomputers) automatisch worden vertrouwd voor HTTPS-verbindingen met de sitesysteemservers. Op apparaten die geen lid zijn van het domein (meestal mobiele apparaten) is het vereiste basiscertificaat echter niet geïnstalleerd. Die apparaten moet het basiscertificaat handmatig worden geïnstalleerd op deze kunnen communiceren met sitesysteemservers op ondersteunende\-premises Mobile Device Management.  

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
 Registratie van apparaten voor inschakelen op\-lokaal beheer van mobiele apparaten, gebruikers moeten machtigingen verlenen voor het inschrijven en hun apparaten moeten kunnen een vertrouwde communicatie met de sitesysteemservers die als host fungeert voor de vereiste sitesysteemrollen.  

 Gebruikers machtigen kan worden bereikt door het instellen van een inschrijvingsprofiel in de clientinstellingen voor Configuration Manager. U kunt de standaardclientinstellingen gebruiken om het inschrijvingsprofiel naar alle gedetecteerde gebruikers te pushen of u kunt het inschrijvingsprofiel configureren in de aangepaste clientinstellingen en de instellingen naar een of meer gebruikersverzamelingen pushen.  

 Wanneer de gebruikers zijn gemachtigd om de apparaten in te schrijven, kunnen de gebruikers hun eigen apparaten inschrijven. Als de gebruikers hun apparaat willen inschrijven, moet dit beschikken over het basiscertificaat van de certificeringsinstantie (CA) die het webservercertificaat heeft uitgegeven dat wordt gebruikt op de sitesysteemservers die als host fungeren voor de vereiste sitesysteemrollen.  

 U kunt in plaats van de inschrijving door gebruikers ook een pakket voor bulksgewijs inschrijven instellen. Hiermee wordt toegestaan dat het apparaat wordt ingeschreven zonder tussenkomst van de gebruiker. Dit pakket kan aan het apparaat worden geleverd voordat dit is ingericht voor gebruik of nadat het apparaat het OOBE-proces heeft ondergaan.  

 Zie voor meer informatie over het instellen en inschrijven van apparaten:  

-   [Registratie van apparaten instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

-   [Apparaten inschrijven voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)  
