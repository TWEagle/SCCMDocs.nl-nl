---
title: Clients blokkeren | Microsoft-documenten
description: De clienttoegang blokkeren voor systeembeveiliging met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3e323ab90ec4cc274581e19065fd7d81c0c11c35
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-block-clients-in-system-center-configuration-manager"></a>Bepalen of clients worden geblokkeerd in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als een clientcomputer of client mobiel apparaat niet langer vertrouwd is, kunt u de client in de System Center 2012 Configuration Manager-console blokkeert. Geblokkeerde clients worden geweigerd door de Configuration Manager-infrastructuur zodat ze niet kunnen met sitesystemen om te downloaden communiceren, inventarisgegevens te uploaden of of statusberichten te verzenden.  

 U moet een client blokkeren en zijn blokkering opheffen van zijn toegewezen site, liever dan van een secundaire site of een centrale beheersite.  

> [!IMPORTANT]  
>  Hoewel blokkeren in Configuration Manager helpen kan bij de beveiliging van de Configuration Manager-site, zijn niet afhankelijk van deze functie kunt u beveiliging voor de site tegen niet-vertrouwde computers of mobiele apparaten als u clients toestaat te communiceren met sitesystemen via HTTP, omdat een geblokkeerde client de site met een nieuw zelfondertekend certificaat en hardware-ID. opnieuw zou kan vervoegen Gebruik daarentegen de blokkeringsfunctie om verloren of verdachte opstartmedia te blokkeren die u gebruikt om besturingssystemen te implementeren en wanneer sitesystemen HTTPS-clientverbindingen aanvaarden.  

 Clients die toegang hebben tot de site door gebruik te maken van het ISV Proxy-certificaat kunnen niet geblokkeerd worden. Zie de System Center Configuration Manager Software Development Kit (SDK) voor meer informatie over het ISV Proxy-certificaat.  

 Indien uw sitesystemen HTTPS-clientverbindingen aanvaarden en uw openbare-sleutelinfrastructuur (PKI) een certificaatintrekkingslijst (CRL) ondersteunt, beschouw dan altijd certificaatintrekking als uw eerstelijnsverdediging tegen eventueel verdachte certificaten. Blokkeren van clients in Configuration Manager is een tweede verdediging om uw hiërarchie te beschermen.  

##  <a name="BKMK_Block_vs_CRL"></a> Overwegingen voor het blokkeren van clients  

-   Deze optie is beschikbaar voor HTTP- en HTTPS-clientverbindingen, maar biedt beperkte beveiliging als clients verbinding maken met sitesystemen met HTTP.  

-   Configuration Manager-beheerders hebben de bevoegdheid om een client te blokkeren en de actie wordt uitgevoerd in de Configuration Manager-console.  

-   Clientcommunicatie is uit de hiërarchie van Configuration Manager alleen geweigerd.  

    > [!NOTE]  
    >  Dezelfde client zou kunnen registreren met een andere Configuration Manager-hiërarchie.  

-   De client wordt onmiddellijk geblokkeerd vanuit de Configuration Manager-site.  

-   Helpt sitesystemen te beschermen tegen eventueel verdachte computers en mobiele apparaten.  

## <a name="considerations-for-using-certificate-revocation"></a>Overwegingen voor het intrekken van certificaten  

-   De optie is beschikbaar voor HTTPS-verbindingen van Windows-clients als de openbare-sleutelinfrastructuur een certificaatintrekkingslijst (CRL) ondersteunt.  

     Mac-clients voeren altijd een CRL-controle uit en deze functionaliteit kan niet worden uitgeschakeld.  

     Hoewel mobiele apparaatclients geen certificaatintrekkinglijsten gebruiken om de certificaten voor sitesystemen te controleren, kunnen u hun certificaten ingetrokken en gecontroleerd door Configuration Manager.  

-   Beheerders van openbare-sleutelinfrastructuur hebben de bevoegdheid voor het intrekken van een certificaat en de actie wordt uitgevoerd buiten de Configuration Manager-console.  

-   Clientcommunicatie kan geweigerd worden van elke computer of elk mobiel apparaat dat dit clientcertificaat vereist.  

-   Er is waarschijnlijk een vertraging tussen een certificaat intrekken en sitesystemen die de gewijzigde certificaatintrekkingslijst (CRL) downloaden.  

-   Voor vele PKI-implementaties kan deze vertraging een dag of meer bedragen. In Active Directory Certificate Services bijvoorbeeld is de standaard termijnafloop één week voor een volledige CRM en één dag voor een delta-CRL.  

-   Helpt sitesystemen en clients te beschermen tegen eventueel verdachte computers en mobiele apparaten.  

    > [!NOTE]  
    >  U kunt sitesystemen die IIS uitvoeren verder beschermen tegen onbekende clients door een certificaatvertrouwenslijst (CTL) te configureren in IIS.  

