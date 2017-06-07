---
title: Installatiemethoden voor clients | Microsoft-documenten
description: Informatie over installatiemethoden voor clients voor System Center Configuration Manager.
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: edca31249cc2bb3e0c67265962815c82e3f4711e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>Clientinstallatiemethoden in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt verschillende methoden gebruiken om de Configuration Manager-clientsoftware te installeren. U kunt één methode of een combinatie van methoden gebruiken. In dit onderwerp kunt u meer informatie over elke methode, voor meer informatie over welke methode best zal werken in uw organisatie.  

## <a name="client-push-installation"></a>Clientpushinstallatie  

 **Ondersteunde client-platform:** Windows  

 **Voordelen**  

-   Kan gebruikt worden om de client te installeren op één computer, een verzameling van computers of voor de resultaten van een query.  

-   Kan gebruikt worden om automatisch de client te installeren op alle gedetecteerde computers.  

-   Gebruikt automatisch clientinstallatie-eigenschappen die zijn gedefinieerd op het tabblad **Client** in het dialoogvenster **Clientpushinstallatie-eigenschappen**.  

 **Nadelen**  

-   Kan hoog netwerkverkeer veroorzaken wanneer te grote verzamelingen worden gepusht.  

-   Kan alleen worden gebruikt op computers die zijn gedetecteerd door Configuration Manager.  

-   Kan niet worden gebruikt voor het installeren van clients in een werkgroep.  

-   Er moet een clientpushinstallatie-account opgegeven worden die beheerdersrechten heeft voor de bedoelde clientcomputer.  

-   Windows Firewall moet geconfigureerd zijn op clientcomputers met uitzonderingen zodat clientpushinstallatie vervolledigd kan worden.  

-   U kunt clientpushinstallatie niet annuleren. Wanneer u deze clientinstallatiemethode voor een site gebruikt, wordt Configuration Manager probeert de client te installeren op alle gedetecteerde bronnen en alle mislukte pogingen gedurende 7 dagen.  

 Zie [Clients implementeren op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md) voor meer informatie over deze installatiemethode.  

## <a name="software-update-point-based-installation"></a>Installatie op basis van software-updatepunten  
 **Ondersteunde client-platform:** Windows  

 **Voordelen:**  

-   Kan uw bestaande software-update-infrastructuur gebruiken om de clientsoftware te beheren.  

-   Kan automatisch de clientsoftware installeren op nieuwe computers als Windows Server Update Services (WSUS) en instellingen voor groepsbeleid in Active Directory Domain Services juist geconfigureerd zijn.  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Zal de clientsoftware opnieuw installeren als hij wordt verwijderd.  

-   Vereist niet dat u een installatie-account configureert en onderhoudt voor de bedoelde clientcomputer.  

 **Nadelen:**  

-   Vereist een werkende software-update-infrastructuur als een vereist onderdeel.  

-   Moet dezelfde server gebruiken voor clientinstallatie en software-updates en deze server moet zich bevinden op een primaire site.  

-   Als u nieuwe clients wilt installeren, moet u een groepsbeleidobject (GPO) configureren in Active Directory Domain Services met het actieve software-updatepunt en de actieve updatepoort van de client.  

-   Indien het Active Directory-schema voor Configuration Manager niet is uitgebreid, moet u groepsbeleidinstellingen gebruiken om van computers met clientinstallatie-eigenschappen.  

 Zie [Clients implementeren op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md) voor meer informatie over deze installatiemethode.  

## <a name="group-policy-installation"></a>Installatie van Groepsbeleid  
 **Ondersteunde client-platform:** Windows  

 **Voordelen:**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Vereist niet dat u een installatie-account configureert en onderhoudt voor de bedoelde clientcomputer.  

 **Nadelen:**  

-   Kan veel netwerkverkeer veroorzaken indien een groot aantal clients worden geïnstalleerd.  

-   Indien het Active Directory-schema voor Configuration Manager niet is uitgebreid, moet u groepsbeleidinstellingen gebruiken om toe te voegen clientinstallatie-eigenschappen op computers in uw site.  

 Zie [Clients implementeren op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md) voor meer informatie over deze installatiemethode.  

## <a name="logon-script-installation"></a>Aanmeldingscriptinstallatie  
 **Ondersteunde client-platform:** Windows  

 **Voordelen:**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen:**  

-   Kan veel netwerkverkeer veroorzaken indien een groot aantal clients in een korte tijdspanne worden geïnstalleerd.  

-   Kan lange tijd duren om te installeren op alle clientcomputers indien gebruikers zich niet frequent aanmelden op het netwerk.  

 Zie [Clients implementeren op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md) voor meer informatie over deze installatiemethode.  

## <a name="manual-installation"></a>Handmatige installatie  
 **Ondersteunde client-platform:** Windows-, UNIX/Linux, Mac OS X  

 **Voordelen:**  

-   Vereist niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan handig zijn voor testdoeleinden.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

 **Nadelen:**  

-   Er is geen automatisering, dus tijdrovend.  

 Zie de volgende onderwerpen voor meer informatie over het handmatig installeren van de client op de verschillende platforms:  

-   [Het implementeren van clients op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

-   [Clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)  

-   [Clients implementeren in Macs in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  
