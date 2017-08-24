---
title: Content management-beveiliging en privacy | Microsoft Docs
description: Beveiliging en privacy voor inhoudsbeheer in System Center Configuration Manager optimaliseren.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: c4b9d13079c313879c6d43b10867c616fa962668
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-content-management-for-system-center-configuration-manager"></a>Beveiliging en privacy voor inhoudbeheer voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat informatie over de beveiliging en privacy voor inhoudsbeheer in System Center Configuration Manager. Lees het in combinatie met de volgende onderwerpen:  

-   [Beveiliging en privacy voor Toepassingsbeheer in System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md)  

-   [Beveiliging en privacy voor software-updates in System Center Configuration Manager](/sccm/sum/plan-design/security-and-privacy-for-software-updates)  

-   [Beveiliging en privacy voor besturingssysteemimplementatie in System Center Configuration Manager](../../../osd/plan-design/security-and-privacy-for-operating-system-deployment.md)  

##  <a name="BKMK_Security_ContentManagement"></a> Aanbevolen beveiligingsprocedures voor inhoudsbeheer  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor inhoudsbeheer:  

 **U kunt de voordelen en nadelen van het gebruik van HTTPS en HTTP voor distributiepunten op het intranet,**: In de meeste gevallen bevat met behulp van HTTP en pakkettoegangsaccounts voor autorisatie meer beveiliging dan het gebruik van HTTPS met versleuteling maar zonder autorisatie. Als uw inhoud echter gevoelige gegevens bevat die u tijdens de overdracht wilt versleutelen, gebruikt u HTTPS.  

-   **Als u HTTPS gebruikt voor een distributiepunt**, Configuration Manager geen pakkettoegangsaccounts gebruikt om toegang tot de inhoud te verlenen, maar de inhoud versleuteld wanneer deze via het netwerk wordt overgedragen.  

-   **Wanneer u HTTP gebruikt voor een distributiepunt**, kunt u pakkettoegangsaccounts gebruiken voor autorisatie, maar wordt de inhoud niet versleuteld wanneer deze via het netwerk wordt overgedragen.  


**Als u voor het distributiepunt een PKI-certificaat gebruikt voor clientverificatie in plaats van een zelfondertekend certificaat, moet u het certificaatbestand (.PFX) beschermen met een sterk wachtwoord. Als u het bestand op het netwerk opslaat, beveiligt u het netwerkkanaal wanneer u het bestand in Configuration Manager importeert**: Wanneer u een wachtwoord vereisen om te importeren van het certificaat voor clientverificatie die het distributiepunt gebruikt om te communiceren met beheerpunten, helpt u hiermee het certificaat te beschermen tegen een aanvaller. Server Message Block (SMB) ondertekening of IPsec tussen de netwerklocatie en de siteserver gebruiken om te voorkomen dat aanvallers knoeien met het certificaatbestand.  

**De distributiepuntrol verwijderen van de siteserver**: Een distributiepunt wordt standaard geïnstalleerd op dezelfde server als de siteserver. Clients hoeven niet rechtstreeks met de siteserver te communiceren. Om de kwetsbaarheid te beperken wijst u de distributiepuntrol dus toe aan andere sitesystemen en verwijdert u de rol van de siteserver.  

**Beveilig inhoud op pakkettoegangsniveau**: De distributiepuntshare geeft leestoegang aan alle gebruikers. Als u wilt beperken welke gebruikers toegang hebben tot de inhoud, gebruikt u pakkettoegangsaccounts wanneer het distributiepunt is geconfigureerd voor HTTP. Dit geldt niet voor cloud-gebaseerde distributiepunten, die geen ondersteuning voor pakkettoegangsaccounts bieden. Zie voor meer informatie over pakkettoegangsaccounts [accounts voor toegang tot inhoud beheren](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).


**Als Configuration Manager is IIS geïnstalleerd wanneer u een sitesysteemrol van distributiepunt toevoegt, verwijdert u HTTP-omleiding of IIS Management Scripts en hulpprogramma's als de installatie van het distributiepunt voltooid is**: Het distributiepunt vereist geen HTTP-omleiding of IIS Management Scripts en hulpprogramma's. Verwijder deze rolservices voor de webserverrol (IIS) om de kwetsbaarheid te beperken.  Zie voor meer informatie over de rolservices voor de Webserverrol (IIS) voor distributiepunten [Site en site-systeemvereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).  

**Stel toegangsmachtigingen voor pakket wanneer u het pakket maakt**: Omdat wijzigingen aan de toegangsaccounts voor de pakketbestanden van kracht worden alleen wanneer u het pakket opnieuw distribueert, het pakket toegangsmachtigingen zorgvuldig instellen wanneer u het pakket voor het eerst maakt. Dit is vooral belangrijk als het pakket groot is, het pakket naar veel distributiepunten wordt distribueert en wanneer de bandbreedtecapaciteit van het netwerk voor inhoudsdistributie beperkt is.  

**Implementeren van toegangsbeheer om media met voorbereide inhoud te beveiligen**: Voorbereide inhoud is gecomprimeerd, maar niet versleuteld. Bij een aanval kunnen de bestanden gelezen en gewijzigd worden en vervolgens naar apparaten worden gedownload. Configuration Manager-clients weigeren inhoud waarmee is geknoeid, maar wel gedownload.  

**Importeer voorbereide inhoud met behulp van alleen het opdrachtregelprogramma extractcontent (ExtractContent.exe) dat wordt meegeleverd met Configuration Manager en zorg ervoor dat is ondertekend door Microsoft**: Om geknoei en een verhoging van bevoegdheden voorkomen, gebruikt u alleen het geautoriseerde opdrachtregelprogramma dat wordt meegeleverd met Configuration Manager.  

**Beveilig het communicatiekanaal tussen de siteserver en de locatie van de pakketbron**: Gebruik IPsec of SMB-ondertekening tussen de siteserver en de locatie van de pakketbron wanneer u toepassingen en pakketten maakt. Zo voorkomt u dat een kwaadwillende persoon knoeit met de bronbestanden.  

**Als u de siteoptie-configuratie voor het gebruik van een aangepaste website in plaats van de standaardwebsite na de installatie van distributiepuntrollen wijzigen, verwijdert u de virtuele standaardmappen**: Wanneer u van de standaardwebsite naar een aangepaste website overschakelt, verwijdert Configuration Manager de oude virtuele mappen niet. Verwijder de virtuele mappen die oorspronkelijk door Configuration Manager zijn gemaakt voor de standaardwebsite:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Voor cloud-gebaseerde distributiepunten, uw abonnementsgegevens en certificaten beveiligen**: Wanneer u cloud-gebaseerde distributiepunten gebruikt, beveiligen van waardevolle items, inclusief de gebruikersnaam en het wachtwoord voor uw Azure-abonnement, het Azure-beheercertificaat en servicecertificaat van het cloud-gebaseerd distributiepunt. Sla de certificaten veilig op. Als u via het netwerk erheen bladert wanneer u het distributiepunt in de cloud configureert, gebruikt u IPsec of SMB-ondertekening tussen de sitesysteemserver en de bronlocatie.  

**Voor cloud-gebaseerde distributiepunten: Controleer de vervaldatum van de certificaten voor continuïteit van de service**: Configuration Manager geeft geen waarschuwing wanneer geïmporteerde certificaten voor beheer van de cloud-gebaseerd distributiepunt wijst services zijn verlopen. U moet de vervaldatums onafhankelijk van Configuration Manager bewaken en zorg ervoor dat u vernieuwt en vervolgens de nieuwe certificaten vóór de vervaldatum importeren. Dit is vooral belangrijk als u koopt voor een Configuration Manager cloud-gebaseerde distributiepunt service-certificaat van een externe certificeringsinstantie (CA), omdat u mogelijk extra tijd om een vernieuwd certificaat te verkrijgen.  

 Als beide certificaten vervalt, Cloud Services Manager de statusbericht-ID gegenereerd **9425** en het bestand CloudMgr.log bevat een vermelding die aangeeft dat het certificaat **zich in verlopen staat**, waarbij de vervaldatum ook wordt geregistreerd in UTC.  

## <a name="security-considerations-for-content-management"></a>Beveiligingsoverwegingen voor inhoudsbeheer  
Overweeg het volgende bij het plannen van inhoudsbeheer:  

-   Clients valideren inhoud pas nadat deze is gedownload.  

     Configuration Manager-clients valideren de hash van inhoud pas nadat deze is gedownload naar de clientcache. Als een kwaadwillende persoon knoeit met de lijst met bestanden worden gedownload of met de inhoud zelf, kan het downloadproces een aanzienlijke hoeveelheid netwerkbandbreedte, alleen voor de client de inhoud vervolgens verwijderen wanneer de ongeldige hash wordt aangetroffen duren.  

-   Wanneer u cloud-gebaseerde distributiepunten gebruikt, toegang tot de inhoud automatisch beperkt tot uw onderneming is en u kunt geen toegang niet verder beperken bepaalde gebruikers of groepen.  

-   Wanneer u cloud-gebaseerde distributiepunten gebruikt, kunnen clients worden geverifieerd door het beheerpunt en een Configuration Manager-token vervolgens gebruiken voor toegang tot cloud-gebaseerde distributiepunten. Het token is acht uur lang geldig. Dit betekent dat als u een client blokkeert omdat deze niet langer vertrouwd is, deze blijven kan om inhoud te downloaden van een cloud-gebaseerde distributiepunt totdat de geldigheidsperiode van de token is verlopen. Op dit moment won't het beheerpunt uitgeven van een ander token voor de client omdat de client is geblokkeerd.  

     Als u wilt voorkomen dat een geblokkeerde client downloaden van inhoud binnen dit tijdsbestek van acht uur, u kunt de cloudservice stoppen vanaf de **Cloud** knooppunt **Hiërarchieconfiguratie**, in de **beheer** werkruimte in de Configuration Manager-console.  

##  <a name="BKMK_Privacy_ContentManagement"></a> Informatie over privacy voor inhoudsbeheer  
 Configuration Manager bevat geen geen gebruikersgegevens toegevoegd aan inhoudsbestanden, hoewel een gebruiker met beheerdersrechten kiezen mogelijk om dit te doen.  

 Voordat u inhoudsbeheer configureert, moet u nadenken over uw privacyvereisten.  
