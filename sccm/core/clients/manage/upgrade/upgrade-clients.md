---
title: Clients upgraden | Microsoft-documenten
description: Lees de informatie over het bijwerken van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 4b80e0e688dd6482bc9a7fe111607e258071f45a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-clients-in-system-center-configuration-manager"></a>Clients bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt verschillende methoden gebruiken om de System Center Configuration Manager-clientsoftware op Windows-computers, UNIX- en Linux-servers en Mac-computers te werken. Hier worden de voordelen en nadelen van elke methode.  

> [!TIP]  
>  Als u een upgrade van uw serverinfrastructuur uitvoert vanaf een eerdere versie van Configuration Manager \(zoals Configuration Manager 2007 of System Center 2012 Configuration Manager\), wordt u aangeraden de serverupgrades, inclusief alle updates van Current Branch, uit te voeren voordat u een upgrade uitvoert van de Configuration Manager-clients. Op deze manier u hebt ook de meest recente versie van de clientsoftware.  

## <a name="group-policy-installation"></a>Installatie van Groepsbeleid  
 **Ondersteunde client-platform:** Windows  

 **Voordelen**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden bijgewerkt.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Vereist niet dat u een installatie-account configureert en onderhoudt voor de bedoelde clientcomputer.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken als u een groot aantal clients bijwerkt.  

-   Indien het Active Directory-schema voor Configuration Manager niet is uitgebreid, moet u [instellingen voor groepsbeleid](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP) clientinstallatie-eigenschappen toevoegen aan computers in uw site.  


## <a name="logon-script-installation"></a>Aanmeldingscriptinstallatie  
 **Ondersteunde client-platform:** Windows  

 **Voordelen**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken als u een groot aantal clients in een korte periode bijwerkt.  

-   Kan lang duren om bij te werken van alle clientcomputers indien gebruikers niet frequent met het netwerk aanmelden zich.  

 Zie [Configuration Manager-clients met behulp van aanmeldingsscripts installeren](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript) voor meer informatie.  

## <a name="manual-installation"></a>Handmatige installatie  
 **Ondersteunde client-platform:** Windows-, UNIX/Linus Mac OS X  

 **Voordelen**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden bijgewerkt.  

-   Kan handig zijn voor testdoeleinden.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen**  

-   Er is geen automatisering, dus tijdrovend.  

 Zie de volgende onderwerpen voor meer informatie:  

-   [Configuration Manager-Clients handmatig installeren](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Manual)  

-   [Clients voor Linux en UNIX-servers in System Center Configuration Manager bijwerken](../../../../core/clients/manage/upgrade/upgrade-clients-for-linux-and-unix-servers.md)  

-   [Clients op Mac-computers in System Center Configuration Manager bijwerken](../../../../core/clients/manage/upgrade/upgrade-clients-on-mac-computers.md)  

## <a name="upgrade-installation-application-management"></a>Installatie-upgrade (toepassingsbeheer)  
 **Ondersteunde client-platform:** Windows  

> [!NOTE]  
>  U upgraden Configuration Manager 2007-clients met deze methode niet. In dit scenario kunt u de Configuration Manager-client implementeren als een pakket vanuit de Configuration Manager 2007-site of kunt u automatische Clientupgrade, waarbij automatisch maakt en implementeert een pakket met de meest recente versie van de client.  

 **Voordelen**  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken als u de client te grote verzamelingen distribueert.  

-   Kan enkel gebruikt worden om clientsoftware up te daten op computers die werden gedetecteerd en toegewezen aan de site.  

 Zie [Configuration Manager-clients met behulp van aanmeldingsscripts installeren](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientApp) voor meer informatie.  

## <a name="automatic-client-upgrade"></a>Automatische clientupgrade  

> [!NOTE]  
>  Kan worden gebruikt Configuration Manager 2007-clients bijwerken naar System Center Configuration Manager-clients. Een Configuration Manager 2007-client kan toewijzen aan een Configuration Manager-site, maar kan acties uitvoeren behalve automatische clientupdate.  

 **Ondersteunde client-platform:** Windows  

 **Voordelen**  

-   Kan gebruikt worden om automatisch clients in uw site up to date te laten zijn met de laatste versie.  

-   Minimaal beheer vereist.  

 **Nadelen**  

-   Kan enkel gebruikt worden om de clientsoftware up te daten en kan niet gebruikt worden om een nieuwe client te installeren.  

-   Niet geschikt voor het gelijktijdig updaten van een groot aantal clients.  

-   Is van toepassing op alle clients in de hiërarchie die toegewezen zijn aan een site. Kan niet worden ingedeeld per verzameling.  

-   Beperkte opties voor het plannen.  

 Zie [Clients voor Windows-computers bijwerken in System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) voor meer informatie.  

## <a name="client-testing"></a>Client testen  
 **Ondersteunde client-platform:** Windows  

 **Voordelen**  

-   Kan worden gebruikt voor het testen van nieuwe clientversies in een kleinere pre-productieverzameling.  

-   Bij het testen is voltooid, worden clients in de testomgeving gepromoveerd naar productie en automatisch worden bijgewerkt via de Configuration Manager-site.  

 **Nadelen**  

-   Kan enkel gebruikt worden om de clientsoftware up te daten en kan niet gebruikt worden om een nieuwe client te installeren.  

 [Het testen van clientupgrades in een pre-productieverzameling in System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  

