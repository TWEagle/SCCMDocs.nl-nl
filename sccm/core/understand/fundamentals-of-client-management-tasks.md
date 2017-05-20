---
title: Client management grondbeginselen | Microsoft-documenten
description: Meer informatie over taken die u uitvoert om System Center Configuration Manager-clients te beheren.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86b90b8e591e1ae4f58cb361a5e544db6b09cce1
ms.openlocfilehash: 0fee4f4ba462e59859ac93c4218b67cb26bdd6f6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>De basisbegrippen van clientbeheer voor System Center Configuration Manager-toepassingen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u de System Center Configuration Manager-clients installeert, zijn er verschillende taken die u uitvoert om de clients te beheren.  Enkele van de taken worden uitgevoerd vanuit de Configuration Manager-console. Andere taken worden uitgevoerd vanuit de Configuration Manager-clienttoepassing. De toepassing Configuration Manager-client is met de Configuration Manager-clientsoftware geïnstalleerd.

## <a name="configuration-manager-console-tasks"></a>Consoletaken voor Configuration Manager
 In de Configuration Manager-console kunt u diverse clientbeheertaken uitvoeren:  

-   Toepassingen, software-updates, onderhoudsscripts en besturingssystemen implementeren. Installatie voor een specifieke datum en tijd configureren, maakt u de software beschikbaar voor gebruikers om te installeren wanneer deze zijn aangevraagd of configureren van toepassingen worden verwijderd.  

-   Computers beter beschermen tegen malware en beveiligingsrisico's en u melden wanneer er problemen zijn gedetecteerd.  

-   Definieert de configuratie-instellingen voor clients die u wilt controleren en herstellen als deze niet-compatibel zijn.  

-   Inventarisgegevens van hardware en software verzamelen waaronder het controleren en afstemmen van licentiegegevens van Microsoft.  

-   Computerproblemen oplossen met extern beheer.  

-   Instellingen voor energiebeheer implementeren om het energieverbruik van computers te beheren en controleren.  

De Configuration Manager-console controleert het voorgaande taken in near-realtime. Informatie over de melding en status voor elke taak is beschikbaar in de Configuration Manager-console. Voor het vastleggen van gegevens en historische trends de geïntegreerde rapportagecapaciteiten van SQL Server Reporting Services te gebruiken. Clients verzenden gegevens als de clientstatus naar de site.  Informatie over de clientstatus biedt gegevens over de status van de client en de activiteiten van clients en wordt weergegeven in de console of door de ingebouwde rapporten voor Configuration Manager. Met behulp van deze gegevens kunnen computers worden geïdentificeerd die niet reageren en in sommige gevallen problemen automatisch worden hersteld.  

 Zie [How to manage clients in System Center Configuration Manager](../../core/clients/manage/manage-clients.md) (Clients beheren in System Center Configuration Manager) en [Clients beheren voor Linux- en UNIX-servers in System Center Configuration Manager](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md) voor meer informatie over beheertaken voor clients. Voor meer informatie over het gebruik van rapporten gaat u naar   
            [Inleiding op rapportage in System Center Configuration Manager](../../core/servers/manage/introduction-to-reporting.md).  

## <a name="configuration-manager-client-application"></a>Configuration Manager-clienttoepassing  
 Wanneer u de Configuration Manager-clientsoftware installeert, wordt de Configuration Manager-clienttoepassing te geïnstalleerd. In tegenstelling tot Software Center, wordt de Configuration Manager-clienttoepassing ontworpen voor de helpdesk dan voor de eindgebruiker. Bepaalde configuratie-opties vereisen lokale beheermachtigingen en de meeste opties vereisen technische kennis over de werking van de toepassing Configuration Manager-client. U kunt met behulp van deze toepassing de volgende taken op een client uitvoeren:  

-   Weergave eigenschappen van de client, zoals het buildnummer, de toegewezen site, het beheerpunt waarmee deze communiceert en of de client is via een openbare-sleutelinfrastructuur (PKI)-certificaat of een zelfondertekend certificaat.  

-   Bevestig dat de client met succes een clientbeleid heeft gedownload nadat de client voor het eerst is geïnstalleerd. Controleer ook de clientinstellingen zijn ingeschakeld of uitgeschakeld zoals verwacht, volgens de instellingen die zijn geconfigureerd in de Configuration Manager-console.  

-   Clientacties starten. Bijvoorbeeld, het clientbeleid downloaden als er een recente wijziging in de configuratie in de Configuration Manager-console is en u niet wachten wilt totdat de volgende tijdstip geplande.  

-   Handmatig een client toewijzen aan een Configuration Manager-site of probeer een site te vinden. Geef het Domain Name System (DNS)-achtervoegsel voor beheerpunten die naar DNS publiceren.  

-   De clientcache configureren waarop tijdelijk bestanden worden opgeslagen. Verwijder bestanden in de cache als u meer schijfruimte om software te installeren.  

-   Instellingen configureren voor clientbeheer via internet.  

-   Configuratiebasislijnen weergeven die op de client zijn geïmplementeerd, een conformiteitsevaluatie starten en conformiteitsrapporten weergeven.  

