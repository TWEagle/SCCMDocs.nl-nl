---
title: Linux en UNIX-clients beheren | Microsoft-documenten
description: Clients op Linux en UNIX-servers in System Center Configuration Manager beheren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 689af6998d9454d76d060b89ca1365d328c08020
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Het beheren van clients voor Linux en UNIX-servers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u Linux en UNIX-servers met System Center Configuration Manager beheert, kunt u verzamelingen, onderhoudsvensters en clientinstellingen voor het beheer van de servers configureren. Als op de Configuration Manager-client voor Linux en UNIX geen gebruikersinterface, kunt u ook de client handmatig controleren op de clientbeleid afdwingen.

##  <a name="BKMK_CollectionsforLnU"></a> Collections of Linux and UNIX servers  
 Verzamelingen gebruiken voor het beheren van groepen van Linux en UNIX-servers op dezelfde manier u verzamelingen gebruiken voor het beheren van andere clienttypen. Verzamelingen kunnen niet direct lidmaatschap verzamelingen of query's gebaseerde verzamelingen waarmee client-besturingssystemen, hardwareconfiguraties of andere details weer over de client die zijn opgeslagen in de sitedatabase. U kunt bijvoorbeeld verzamelingen gebruiken die Linux- en UNIX-servers omvatten om het volgende te beheren:  

-   Clientinstellingen  

-   Software-implementatie  

-   Onderhoudsvensters afdwingen  

 Voordat u een client voor Linux of UNIX door het besturingssysteem of een distributiepunt herkennen kunt, moet u verzamelen [hardware-inventaris](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md) van de client.  

 De standaardclientinstellingen voor hardware-inventaris bevatten informatie over het besturingssysteem van de clientcomputer. U kunt de eigenschap **Bijschrift** van de klasse **Besturingssysteem** gebruiken voor het identificeren van het besturingssysteem van een Linux- of UNIX-server.  

 U kunt details weergeven van computers waarop de Configuration Manager-client voor Linux en UNIX wordt uitgevoerd in het knooppunt apparaten van de activa en naleving werkruimte in de Configuration Manager-console. In de werkruimte activa en naleving van de Configuration Manager-console, ziet u de naam van het besturingssysteem van elke computer in de **besturingssysteem** kolom.  

 Standaard maken Linux- en UNIX-servers deel uit van de verzameling **Alle systemen** . Het is raadzaam dat u aangepaste verzamelingen die enkel Linux en UNIX-servers of een subset van deze bevatten maken. Hiermee kunt u voor het beheren van bewerkingen zoals het implementeren van software of toewijzen van de clientinstellingen voor groepen zoals computers, zodat u het succes van een implementatie nauwkeurig kunt meten.   

 Wanneer u een aangepaste verzameling voor Linux- en UNIX-servers maakt, neem daarin dan lidmaatschapregelquery's op met het kenmerk Bijschrift voor het kenmerk Besturingssysteem. Zie voor meer informatie over het maken van verzamelingen [het maken van verzamelingen in System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Maintenance windows for Linux and UNIX servers  
 De Configuration Manager-client voor Linux en UNIX-servers ondersteunt het gebruik van [onderhoudsvensters](../../../core/clients/manage/collections/use-maintenance-windows.md). Deze ondersteuning is ongewijzigd ten opzichte van die voor Windows-clients.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Client settings for Linux and UNIX servers  
 U kunt [clientinstellingen configureren](../../../core/clients/deploy/configure-client-settings.md) die van toepassing op Linux en UNIX-servers dezelfde manier als u instellingen configureren voor andere clients.  

 **Standaard clientagentinstellingen** is standaard van toepassing op Linux- en UNIX-servers. U kunt ook aangepaste clientinstellingen maken en deze implementeren naar verzamelingen van specifieke clients.  

 Er zijn geen aanvullende clientinstellingen die alleen van toepassing zijn op Linux- en UNIX-clients. Er zijn echter standaardclientinstellingen die niet van toepassing zijn op Linux- en UNIX-clients. De client voor Linux en UNIX-instellingen voor functionaliteit die ondersteunt is alleen van toepassing.  

 Een aangepaste clientapparaatinstelling die u maakt en configureert u de instellingen voor extern beheer zou bijvoorbeeld worden genegeerd door de Linux- en UNIX-servers, omdat de client voor Linux en UNIX biedt geen ondersteuning voor beheer op afstand.  

##  <a name="BKMK_PolicyforLnU"></a> Computer policy for Linux and UNIX servers  
 De client voor Linux en UNIX-servers, controleert regelmatig of de site voor computerbeleid voor meer informatie over vereiste configuraties en om te controleren voor implementaties.  

 Ook kunt u de client op een Linux- of UNIX-server dwingen onmiddellijk naar computerbeleid te pollen. Gebruiken om dit te doen, **root** referenties op de server de volgende opdracht uit te voeren: **/opt/microsoft/configmgr/bin/ccmexec rs - beleid**  

 Details over de computerbeleidpoll worden ingevoerd in het logboekbestand van de gedeelde client; **scxcm.log**.  

> [!NOTE]  
>  De Configuration Manager-client voor Linux en UNIX nooit vraagt noch gebruikersbeleid verwerkt.  

##  <a name="BKMK_ManageLinuxCerts"></a> How to manage certificates on the client for Linux and UNIX  
 Nadat u de client voor Linux en UNIX hebt geïnstalleerd, kunt u het hulpprogramma **certutil** gebruiken om de client bij te werken met een nieuw PKI-certificaat, en om een nieuwe certificaatintrekkingslijst (CRL) te importeren. Wanneer u de client voor Linux en UNIX installeert, wordt dit hulpprogramma geplaatst **/opt/microsoft/configmgr/bin/certutil**. 

 Om certificaten te beheren, voert u elke client certutil met een van de volgende opties uit:  

|Optie|Meer informatie|  
|------------|----------------------|  
|importPFX|Gebruik deze optie om een certificaat op te geven ter vervanging van het certificaat dat momenteel door een client wordt gebruikt.<br /><br /> Bij het gebruik van **- importPFX**, moet u ook gebruiken de **-wachtwoord** opdrachtregelparameter het wachtwoord dat is gekoppeld aan de PKCS #12-bestand op te geven.<br /><br /> Gebruik **-rootcerts** om eventuele extra vereisten voor basiscertificaten op te geven.<br /><br /> Voorbeeld: **certutil - importPFX &lt;pad naar het certificaat van PKCS #12 >-wachtwoord &lt;certificaatwachtwoord\> [-rootcerts &lt;met door komma's gescheiden lijst van certificaten >]**|  
|-importsitecert|Gebruik deze optie om het ondertekeningscertificaat voor de siteserver bij te werken dat zich op beheerserver bevindt.<br /><br /> Voorbeeld: **certutil - importsitecert &lt;pad naar het certificaat DER\>**|  
|-importcrl|Gebruik deze optie om de certificaatintrekkingslijst op de client bij te werken met een of meer paden naar certificaatintrekkingslijstbestanden.<br /><br /> Voorbeeld: **certutil - importcrl &lt;met door komma's gescheiden paden CRL\>**|  

