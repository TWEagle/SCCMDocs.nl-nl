---
title: Upgrade uitvoeren voor clients | Microsoft Docs
description: Informatie ophalen over het upgraden van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
caps.latest.revision: "8"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 80665e0369880bc6c46a76b22c9c89f068df1b0d
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="upgrade-clients-in-system-center-configuration-manager"></a>Clients bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt verschillende methoden gebruiken om de System Center Configuration Manager-clientsoftware op Windows-computers, UNIX en Linux-servers en Mac-computers te werken. Hier volgen de voordelen en nadelen van elke methode.  

> [!TIP]  
>  Als u een upgrade van uw serverinfrastructuur uitvoert vanaf een eerdere versie van Configuration Manager \(zoals Configuration Manager 2007 of System Center 2012 Configuration Manager\), wordt u aangeraden de serverupgrades, inclusief alle updates van Current Branch, uit te voeren voordat u een upgrade uitvoert van de Configuration Manager-clients. Op deze manier ook hebt u de meest recente versie van de clientsoftware.  

## <a name="group-policy-installation"></a>Installatie van Groepsbeleid  
 **Ondersteund clientplatform:** Windows  

 **Voordelen**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden bijgewerkt.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Vereist niet dat u een installatie-account configureert en onderhoudt voor de bedoelde clientcomputer.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken indien u een een groot aantal clients upgrade uitvoert.  

-   Als de Active Directory-schema voor Configuration Manager niet is uitgebreid, moet u [instellingen voor groepsbeleid](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientGP) clientinstallatie-eigenschappen toevoegen aan computers in uw site.  


## <a name="logon-script-installation"></a>Aanmeldingscriptinstallatie  
 **Ondersteund clientplatform:** Windows  

 **Voordelen**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken indien u een van clients in korte tijd veel upgrade uitvoert.  

-   Kan lang duren om bij te werken van alle clientcomputers indien gebruikers zich niet regelmatig op met het netwerk aanmelden.  

 Zie [Configuration Manager-clients met behulp van aanmeldingsscripts installeren](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientLogonScript) voor meer informatie.  

## <a name="manual-installation"></a>Handmatige installatie  
 **Ondersteund clientplatform:** Windows, UNIX/Linus, Mac OS X  

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
 **Ondersteund clientplatform:** Windows  

> [!NOTE]  
>  U kunt Configuration Manager 2007-clients niet bijwerken met deze methode. In dit scenario kunt u de Configuration Manager-client implementeren als een pakket vanuit de Configuration Manager 2007-site of kunt u automatische Clientupgrade, waarbij automatisch maakt en implementeert een pakket met de meest recente versie van de client.  

 **Voordelen**  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken als u de client te grote verzamelingen distribueert.  

-   Kan enkel gebruikt worden om clientsoftware up te daten op computers die werden gedetecteerd en toegewezen aan de site.  

 Zie [Configuration Manager-clients met behulp van aanmeldingsscripts installeren](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientApp) voor meer informatie.  

## <a name="automatic-client-upgrade"></a>Automatische clientupgrade  

> [!NOTE]  
>  Configuration Manager 2007-clients upgraden naar System Center Configuration Manager-clients kan worden gebruikt. Een Configuration Manager 2007-client kan toewijzen aan een Configuration Manager-site, maar kan acties uitvoeren behalve automatische Clientupgrade.  

 **Ondersteund clientplatform:** Windows  

 **Voordelen**  

-   Kan gebruikt worden om automatisch clients in uw site up to date te laten zijn met de laatste versie.  

-   Vereist minimaal beheer.  

 **Nadelen**  

-   Kan enkel gebruikt worden om de clientsoftware up te daten en kan niet gebruikt worden om een nieuwe client te installeren.  

-   Niet geschikt voor het gelijktijdig updaten van een groot aantal clients.  

-   Is van toepassing op alle clients in de hiërarchie die toegewezen zijn aan een site. Kan niet worden ingedeeld per verzameling.  

-   Beperkte opties voor het plannen.  

 Zie [Clients voor Windows-computers bijwerken in System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) voor meer informatie.  

## <a name="client-testing"></a>Client testen  
 **Ondersteund clientplatform:** Windows  

 **Voordelen**  

-   Kan worden gebruikt voor het testen van nieuwe clientversies in kleinere pre-productieverzameling.  

-   Wanneer de test is voltooid, worden clients vóór productie verhoogd naar productie en automatisch bijgewerkt op de Configuration Manager-site.  

 **Nadelen**  

-   Kan enkel gebruikt worden om de clientsoftware up te daten en kan niet gebruikt worden om een nieuwe client te installeren.  

 [Clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md)  
