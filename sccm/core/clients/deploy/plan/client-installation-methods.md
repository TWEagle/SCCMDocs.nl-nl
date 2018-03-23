---
title: Clientinstallatiemethoden
titleSuffix: Configuration Manager
description: Meer informatie over de methoden voor het installeren van Configuration Manager-client.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 38f7d428149f4a4ac2b0bcb604031eca60a0fae5
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="client-installation-methods-in-system-center-configuration-manager"></a>Clientinstallatiemethoden in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt verschillende methoden gebruiken om de Configuration Manager-clientsoftware te installeren. Een methode of een combinatie van methoden gebruiken. In dit artikel beschrijft elke methode zodat u leert welk werkt het beste voor uw organisatie.  

## <a name="client-push-installation"></a>Clientpushinstallatie  

**Ondersteund clientplatform**: Windows  

#### <a name="advantages"></a>Voordelen  

-   Kan gebruikt worden om de client te installeren op één computer, een verzameling van computers of voor de resultaten van een query.  

-   Kan gebruikt worden om automatisch de client te installeren op alle gedetecteerde computers.  

-   Gebruikt automatisch clientinstallatie-eigenschappen die zijn gedefinieerd op het tabblad **Client** in het dialoogvenster **Clientpushinstallatie-eigenschappen**.  

#### <a name="disadvantages"></a>Nadelen  

-   Kan hoog netwerkverkeer veroorzaken wanneer te grote verzamelingen worden gepusht.  

-   Kan alleen worden gebruikt op computers die door Configuration Manager zijn gedetecteerd.  

-   Kan niet worden gebruikt voor het installeren van clients in een werkgroep.  

-   Er moet een clientpushinstallatie-account opgegeven worden die beheerdersrechten heeft voor de bedoelde clientcomputer.  

-   Windows Firewall moet zijn geconfigureerd met uitzonderingen op clientcomputers.   

-   U kunt clientpushinstallatie niet annuleren. Configuration Manager probeert de client te installeren op alle gedetecteerde bronnen. Deze pogingen alle mislukte tot zeven dagen.  

Zie voor meer informatie [clients installeren met client-push](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush).  



## <a name="software-update-point-based-installation"></a>Installatie op basis van software-updatepunten  

**Ondersteund clientplatform**: Windows  

#### <a name="advantages"></a>Voordelen  

-   Kan uw bestaande software-update-infrastructuur gebruiken om de clientsoftware te beheren.  

-   Als Windows Server Update Services (WSUS) en instellingen voor Groepsbeleid in Active Directory Domain Services juist zijn geconfigureerd, kan deze automatisch de clientsoftware installeren op nieuwe computers.  

-   Niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Als de client wordt verwijderd, wordt deze methode wordt opnieuw geïnstalleerd.  

-   Hoeft u configureert en onderhoudt een installatie-account voor de bedoelde clientcomputer.  

#### <a name="disadvantages"></a>Nadelen  

-   Vereist een werkende software-update-infrastructuur als een vereist onderdeel.  

-   Moet dezelfde server gebruiken voor clientinstallatie en software-updates. Deze server moet zich bevinden in een primaire site.  

-   Voor het installeren van nieuwe clients, moet u een groepsbeleidobject in Active Directory Domain Services configureren met het actieve software-updatepunt en de poort van de client.  

-   Als het Active Directory-schema niet is uitgebreid voor Configuration Manager, moet u groepsbeleidinstellingen voor het inrichten van computers met clientinstallatie-eigenschappen.  

Zie voor meer informatie [clients installeren met software-update-gebaseerde installatie](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientSUP).  



## <a name="group-policy-installation"></a>Installatie van Groepsbeleid  

**Ondersteund clientplatform**: Windows  

#### <a name="advantages"></a>Voordelen  

-   Niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan worden gebruikt voor de nieuwe clientinstallaties of voor upgrades.  

-   Computers kunnen clientinstallatie-eigenschappen lezen die gepubliceerd werden op Active Directory Domain Services.  

-   Hoeft u configureert en onderhoudt een installatie-account voor de bedoelde clientcomputer.  

#### <a name="disadvantages"></a>Nadelen  

-   Indien een groot aantal clients worden geïnstalleerd, kan dit veel netwerkverkeer veroorzaken.  

-   Als het Active Directory-schema niet is uitgebreid voor Configuration Manager, moet u instellingen voor Groepsbeleid clientinstallatie-eigenschappen toevoegen aan computers in uw site.  

Zie voor meer informatie [clients installeren met het groepsbeleid](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientGP).  



## <a name="logon-script-installation"></a>Aanmeldingscriptinstallatie  

**Ondersteund clientplatform**: Windows  

#### <a name="advantages"></a>Voordelen  

-   Niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

#### <a name="disadvantages"></a>Nadelen  

-   Indien een groot aantal clients in een korte tijdspanne worden geïnstalleerd, kan dit veel netwerkverkeer veroorzaken.  

-   Als gebruikers niet frequent op het netwerk aanmelden, kan het lang duren om te installeren op alle clientcomputers.  

Zie voor meer informatie [clients installeren met aanmeldingsscripts](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientLogonScript).  



## <a name="manual-installation"></a>Handmatige installatie  

**Ondersteund clientplatform**: Windows, UNIX/Linux, Mac OS X  

#### <a name="advantages"></a>Voordelen  

-   Niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Kan handig zijn voor testdoeleinden.  

-   Ondersteunt opdrachtregeleigenschappen voor CCMSetup.  

#### <a name="disadvantages"></a>Nadelen  

-   Er is geen automatisering, dus tijdrovend.  

Zie de volgende artikelen voor meer informatie over het handmatig installeren van de client op verschillende platforms:  

-   [Clients implementeren op Windows-computers](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)  

-   [Clients implementeren op UNIX- en Linux-servers](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)  

-   [Clients op Macs implementeren](/sccm/core/clients/deploy/deploy-clients-to-macs)  



## <a name="microsoft-intune-mdm-installation"></a>Microsoft Intune MDM-installatie

**Ondersteunde clientplatforms voor**: Windows 10

#### <a name="advantages"></a>Voordelen  

-   Niet dat computers moeten worden gedetecteerd voordat de client kan worden geïnstalleerd.  

-   Hoeft u configureert en onderhoudt een installatie-account voor de bedoelde clientcomputer.  

-   Kan moderne authenticatie gebruiken met Azure Active Directory.  

-   Kunt installeren en toewijzen van computers op het internet.  

-   Kunt automatiseren met Windows Automatische piloot en Microsoft Intune voor het beheer van collega.  

#### <a name="disadvantages"></a>Nadelen  

-   Vereist aanvullende technologieën buiten Configuration Manager.  

-   Moet het apparaat toegang tot internet, zelfs als het is niet op basis van het internet.  

Zie voor meer informatie de volgende artikelen:  

-   [Het installeren van clients op Windows Intune MDM-beheerde apparaten](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#bkmk_mdm)  

-   [Installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

