---
title: Linux- en UNIX-clients beheren | Microsoft Docs
description: Clients op Linux en UNIX-servers in System Center Configuration Manager beheren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
caps.latest.revision: "7"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 506df4f7c7baa5f0586a1ddf0cb02b3de9f4d076
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Clients voor Linux en UNIX-servers in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u Linux en UNIX-servers met System Center Configuration Manager beheert, kunt u verzamelingen, onderhoudsvensters en clientinstellingen voor de servers te beheren. Hoewel de Configuration Manager-client voor Linux en UNIX geen gebruikersinterface heeft, kunt u ook de client handmatig poll-frequentie voor clientbeleid afdwingen.

##  <a name="BKMK_CollectionsforLnU"></a> Collections of Linux and UNIX servers  
 Verzamelingen gebruiken voor het beheren van groepen van Linux en UNIX-servers op dezelfde manier u verzamelingen gebruiken voor het beheren van andere clienttypen. Verzamelingen kunnen directe lidmaatschapverzamelingen of query's gebaseerde verzamelingen zijn. Query's gebaseerde verzamelingen identificeren clientbesturingssystemen, hardwareconfiguraties of andere details over de client die zijn opgeslagen in de sitedatabase. U kunt bijvoorbeeld verzamelingen met Linux en UNIX-servers voor het beheren van de volgende instellingen:  

-   Clientinstellingen  

-   Software-implementatie  

-   Onderhoudsvensters afdwingen  

 Voordat u een Linux- of UNIX-client door het besturingssysteem of distributie identificeren kunt, moet u verzamelt [hardware-inventaris](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) van de client.  

 De standaardclientinstellingen voor hardware-inventarisatie bevatten informatie over het besturingssysteem van een clientcomputer. U kunt de eigenschap **Bijschrift** van de klasse **Besturingssysteem** gebruiken voor het identificeren van het besturingssysteem van een Linux- of UNIX-server.  

 U kunt details zien over computers met de Configuration Manager-client voor Linux en UNIX in de **apparaten** knooppunt van de **activa en naleving** werkruimte in de Configuration Manager-console. In de **activa en naleving** werkruimte van de Configuration Manager-console vindt u de naam van het besturingssysteem van elke computer in de **besturingssysteem** kolom.  

 Standaard maken Linux- en UNIX-servers deel uit van de verzameling **Alle systemen** . Het is raadzaam dat u aangepaste verzamelingen maakt die alleen Linux en UNIX-servers of een subset ervan. Aangepaste verzamelingen kunnen u bewerkingen beheren zoals het implementeren van software of toewijzen van clientinstellingen aan groepen zoals computers, zodat u het succes van een implementatie nauwkeurig kunt meten.   

 Wanneer u een aangepaste verzameling voor Linux- en UNIX-servers maakt, neem daarin dan lidmaatschapregelquery's op met het kenmerk Bijschrift voor het kenmerk Besturingssysteem. Zie voor meer informatie over het maken van verzamelingen [verzamelingen maken in System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Maintenance windows for Linux and UNIX servers  
 De Configuration Manager-client voor Linux en UNIX-servers ondersteunt het gebruik van [onderhoudsvensters](../../../core/clients/manage/collections/use-maintenance-windows.md). Deze ondersteuning is ongewijzigd ten opzichte van Windows-clients.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Client settings for Linux and UNIX servers  
 U kunt [clientinstellingen configureren](../../../core/clients/deploy/configure-client-settings.md) die gelden voor Linux en UNIX-servers dezelfde manier als u instellingen configureren voor andere clients.  

 **Standaard clientagentinstellingen** is standaard van toepassing op Linux- en UNIX-servers. U kunt ook aangepaste clientinstellingen maken en deze implementeren naar verzamelingen van specifieke clients.  

 Er zijn geen aanvullende clientinstellingen die alleen van toepassing zijn op Linux- en UNIX-clients. Er zijn echter standaardclientinstellingen die niet van toepassing zijn op Linux- en UNIX-clients. De client voor Linux en UNIX past alleen instellingen voor functionaliteit die wordt ondersteund.  

 Bijvoorbeeld zou een aangepaste clientapparaatinstelling die mogelijk maakt en configureert instellingen voor extern beheer door de Linux- en UNIX-servers, worden genegeerd omdat de client voor Linux en UNIX geen ondersteuning biedt voor beheer op afstand.  

##  <a name="BKMK_PolicyforLnU"></a> Computer policy for Linux and UNIX servers  
 De client voor Linux en UNIX-servers periodiek de site naar computerbeleid voor meer informatie over vereiste configuraties en implementaties te controleren.  

 Ook kunt u de client op een Linux- of UNIX-server dwingen onmiddellijk naar computerbeleid te pollen. Gebruiken om dit te doen **hoofdmap** referenties op de server de volgende opdracht uitvoeren: **/opt/microsoft/configmgr/bin/ccmexec - rs beleid**  

 Details over de computerbeleidpoll worden ingevoerd in het logboekbestand van de gedeelde client; **scxcm.log**.  

> [!NOTE]  
>  Configuration Manager-client voor Linux en UNIX nooit aanvragen noch gebruikersbeleid verwerkt.  

##  <a name="BKMK_ManageLinuxCerts"></a> How to manage certificates on the client for Linux and UNIX  
 Nadat u de client voor Linux en UNIX hebt geïnstalleerd, kunt u het hulpprogramma **certutil** gebruiken om de client bij te werken met een nieuw PKI-certificaat, en om een nieuwe certificaatintrekkingslijst (CRL) te importeren. Wanneer u de client voor Linux en UNIX installeert, dit hulpprogramma wordt geplaatst in **/opt/microsoft/configmgr/bin/certutil**. 

 Om certificaten te beheren, voert u elke client certutil met een van de volgende opties uit:  

|Optie|Meer informatie|  
|------------|----------------------|  
|importPFX|Gebruik deze optie om een certificaat op te geven ter vervanging van het certificaat dat momenteel door een client wordt gebruikt.<br /><br /> Als u werkt met **- importPFX**, moet u ook gebruiken de **-wachtwoord** opdrachtregelparameter het wachtwoord die zijn gekoppeld aan het PKCS #12-bestand op te geven.<br /><br /> Gebruik **-rootcerts** om eventuele extra vereisten voor basiscertificaten op te geven.<br /><br /> Voorbeeld: **certutil - importPFX &lt;pad naar het PKCS #12-certificaat >-wachtwoord &lt;certificaatwachtwoord\> [-rootcerts &lt;door komma's gescheiden lijst met certificaten >]**|  
|-importsitecert|Gebruik deze optie om het ondertekeningscertificaat voor de siteserver bij te werken dat zich op beheerserver bevindt.<br /><br /> Voorbeeld: **certutil - importsitecert &lt;pad naar het certificaat DER\>**|  
|-importcrl|Gebruik deze optie om de certificaatintrekkingslijst op de client bij te werken met een of meer paden naar certificaatintrekkingslijstbestanden.<br /><br /> Voorbeeld: **certutil - importcrl &lt;door komma's gescheiden paden CRL\>**|  
