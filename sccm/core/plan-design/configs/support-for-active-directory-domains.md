---
title: Active Directory-domeinen ondersteund | Microsoft-documenten
description: Vereisten voor het lidmaatschap van een System Center Configuration Manager-sitesysteem ophalen in Active Directory-domein.
ms.custom: na
ms.date: 3/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f397efe458fd85124d2a83d4a869642015fd4a5
ms.openlocfilehash: 2654ab4eaaaf6a4bf3bd7dca9908e7033647dc2c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-active-directory-domains-for-system-center-configuration-manager"></a>Ondersteunde Active Directory-domeinen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Alle System Center Configuration Manager-sitesystemen moeten lid zijn van een ondersteunde Windows Server Active Directory-domein. Configuration Manager-clientcomputers kunnen worden leden van een domein of werkgroepleden.  

 **Vereisten en beperkingen:**  

-   Lidmaatschap van domein geldt voor sitesystemen die clientbeheer via Internet in een perimeternetwerk (ook wel een DMZ, gedemilitariseerde zone en gescreend subnet genoemd ondersteunen).  

-   Wijzig de volgende voor een computer die als host fungeert voor een sitesysteemrol wordt niet ondersteund:  

    -   Lidmaatschap van domein  

    -   Domeinnaam  

    -   Computernaam  

U moet de sitesysteemrol (met inbegrip van de site als het een siteserver) verwijderen voordat u deze wijzigingen aanbrengt.  

**Domeinen met de volgende functionaliteitsniveaus worden ondersteund:**  
- Windows Server 2016

- Windows Server 2012 R2  

- Windows Server 2012

- Windows Server 2008 R2

- Windows Server 2008  







##  <a name="bkmk_Disjoint"></a> Niet-aaneengesloten naamruimte  
Configuration Manager ondersteunt installeren sitesystemen en clients in een domein met een onafhankelijke naamruimte.  

Een niet-aaneengesloten naamruimte scenario is een waarin het primaire Domain Name System (DNS)-achtervoegsel van een computer komt niet overeen met de Active Directory-DNS-domeinnaam waarop deze computer zich bevindt. De computer die gebruikmaakt van het primaire DNS-achtervoegsel komt niet overeen met niet-aaneengesloten genoemd. Een ander niet-aaneengesloten naamruimte scenario treedt op als de NetBIOS-naam van een domeincontroller komt niet overeen met de Active Directory-DNS-domeinnaam.  

In de volgende tabel worden de ondersteunde scenario's voor een ontkoppelde naamruimte vermeld.  

|Scenario|Meer informatie|  
|--------------|----------------------|  
|**Scenario 1:**<br /><br /> Het achtervoegsel van de primaire DNS van de domeincontroller verschilt van de DNS-naam van het Active Directory-domein. Computers die lid van het domein zijn, kunnen ontkoppeld of niet-ontkoppeld zijn.|In dit scenario verschilt het achtervoegsel van de primaire DNS van de domeincontroller van de DNS-naam van het Active Directory-domein. De domeincontroller is in dit scenario ontkoppeld. Computers die lid zijn van het domein, zoals siteservers en computers, kunnen een achtervoegsel voor de primaire DNS hebben die overeenkomt met het achtervoegsel voor de primaire DNS van de domeincontroller of die overeenkomt met de DNS-naam van het Active Directory-domein.|  
|**Scenario 2:**<br /><br /> Een computer die lid is van een Active Directory-domein is ontkoppeld, zelfs al is de domeincontroller niet ontkoppeld.|In dit scenario verschilt het achtervoegsel van de primaire DNS van een lidcomputer waarop een sitesysteem is geïnstalleerd van de DNS-naam van het Active Directory-domein, ook al is het achtervoegsel voor de primaire DNS van de domeincontroller hetzelfde als de DNS-naam van het Active Directory-domein. In dit scenario is er sprake van een domeincontroller die niet ontkoppeld is en een lidcomputer die ontkoppeld is. Computers die lid zijn met de Configuration Manager-client kunnen een primaire DNS-achtervoegsel dat overeenkomt met het primaire DNS-achtervoegsel van de onafhankelijke sitesysteemserver of komt overeen met de Active Directory, DNS-naam hebben.|  

 Als u toegang van een computer tot ontkoppelde domeincontrollers wilt toestaan, moet u het Active Directory-kenmerk in **msDS-AllowedDNSSuffixes** wijzigen in de container voor het domeinobject. U moet beide DNS-achtervoegsels toevoegen aan het kenmerk.  

 Om ervoor te zorgen dat de zoeklijst voor DNS-achtervoegsels bevat alle DNS-naamruimten die binnen de organisatie zijn geïmplementeerd, moet u bovendien de zoeklijst voor elke computer configureren in het domein dat niet-aaneengesloten is. Zorg ervoor dat u het volgende in de lijst met naamruimten: het primaire DNS-achtervoegsel van de domeincontroller, de DNS-domeinnaam en eventuele aanvullende naamruimten voor Configuration Manager met samenwerken kunnen andere servers. U kunt de **zoeklijst voor DNS-achtervoegsels (Domain Name System)** configureren met de console Groepsbeleidsbeheer.  

> [!IMPORTANT]  
>  Wanneer u verwijst naar een computer in Configuration Manager, typt u de computer met behulp van het primaire DNS-achtervoegsel. Dit achtervoegsel moet overeenkomen met de FQDN-naam die is geregistreerd als de **dnsHostName** kenmerk in de Active Directory-domein en de Service-Principal-naam die is gekoppeld aan het systeem.  

##  <a name="bkmk_SLD"></a> Domeinen met een enkelvoudig label  
 Configuration Manager biedt ondersteuning voor sitesystemen en klanten in een domein met één label wanneer wordt voldaan aan de volgende criteria:  

-   Het domein met één label in Active Directory Domain Services moet worden geconfigureerd met een onafhankelijke DNS-naamruimte met een geldig domein op het hoogste niveau.  

     **Bijvoorbeeld:** Het domein enkelvoudige van Contoso is geconfigureerd om een niet-aaneengesloten naamruimte in DNS contoso.com. Daarom wanneer u het DNS-achtervoegsel in Configuration Manager voor een computer in de Contoso-domein, geeft u "Contoso.com" en niet 'Contoso'.  

-   De verbindingen Distributed Component Object Model (DCOM) tussen siteservers in de systeemcontext moeten zijn gelukt met behulp van Kerberos-verificatie.  

