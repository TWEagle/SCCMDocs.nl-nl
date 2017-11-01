---
title: De grondbeginselen van de client-management
titleSuffix: Configuration Manager
description: Meer informatie over taken die u voor het beheren van System Center Configuration Manager-clients worden uitgevoerd.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a88be6397e1e2b1f86a517d2c068e1c0cb8a40bc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>De basisbegrippen van clientbeheer voor System Center Configuration Manager-toepassingen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u de System Center Configuration Manager-clients hebt geïnstalleerd, zijn er verschillende taken die u uitvoert om de clients te beheren.  Enkele van de taken worden uitgevoerd vanuit de Configuration Manager-console. Andere taken worden uitgevoerd van de Configuration Manager-clienttoepassing. De toepassing Configuration Manager-client is geïnstalleerd met de Configuration Manager-clientsoftware.

## <a name="configuration-manager-console-tasks"></a>Consoletaken van Configuration Manager
 In de Configuration Manager-console kunt u diverse clientbeheertaken uitvoeren:  

-   Toepassingen, software-updates, onderhoudsscripts en besturingssystemen implementeren. Installatie voor een specifieke datum en tijd te configureren, de software beschikbaar maken voor gebruikers installeren wanneer ze worden aangevraagd of configureren van toepassingen worden verwijderd.  

-   Computers beter beschermen tegen malware en beveiligingsrisico's en u melden wanneer er problemen zijn gedetecteerd.  

-   Definieer de configuratie-instellingen voor clients die u wilt controleren en herstellen als ze niet compatibel zijn.  

-   Inventarisgegevens van hardware en software verzamelen waaronder het controleren en afstemmen van licentiegegevens van Microsoft.  

-   Computerproblemen oplossen met extern beheer.  

-   Instellingen voor energiebeheer implementeren om het energieverbruik van computers te beheren en controleren.  

De Configuration Manager-console bewaakt de voorgaande taken in bijna realtime. Informatie over Notification en status voor elke taak is beschikbaar in de Configuration Manager-console. Voor het vastleggen van gegevens en historische trends de geïntegreerde rapportagecapaciteiten van SQL Server Reporting Services te gebruiken. Clients verzenden gegevens als de clientstatus naar de site.  Informatie over client biedt gegevens over de status van de client en de clientactiviteit en wordt weergegeven in de console of met behulp van de ingebouwde rapporten voor Configuration Manager. Deze gegevens kunt identificatie van computers die niet reageren en in sommige gevallen problemen automatisch worden hersteld.  

 Zie [How to manage clients in System Center Configuration Manager](../../core/clients/manage/manage-clients.md) (Clients beheren in System Center Configuration Manager) en [Clients beheren voor Linux- en UNIX-servers in System Center Configuration Manager](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md) voor meer informatie over beheertaken voor clients. Voor meer informatie over het gebruik van rapporten gaat u naar   
            [Inleiding op rapportage in System Center Configuration Manager](../../core/servers/manage/introduction-to-reporting.md).  

## <a name="configuration-manager-client-application"></a>Configuration Manager-clienttoepassing  
 Wanneer u de Configuration Manager-clientsoftware installeert, is dat de toepassing Configuration Manager-client te worden geïnstalleerd. In tegenstelling tot Software Center, worden de toepassing Configuration Manager-client is ontworpen voor de helpdesk in plaats van voor de eindgebruiker. Bepaalde configuratie-opties vereisen lokale beheermachtigingen en de meeste opties vereisen technische kennis over de werking van de toepassing Configuration Manager-client. U kunt met behulp van deze toepassing de volgende taken op een client uitvoeren:  

-   Weergave eigenschappen van de client, zoals het buildnummer, de toegewezen site, het beheer beheerpunt waarmee deze communiceert en of de client is via een openbare-sleutelinfrastructuur (PKI)-certificaat of een zelfondertekend certificaat.  

-   Controleer of de client met succes een clientbeleid heeft gedownload nadat de client is geïnstalleerd voor de eerste keer. Controleer ook of de clientinstellingen zijn ingeschakeld of uitgeschakeld zoals verwacht, volgens de clientinstellingen die zijn geconfigureerd in de Configuration Manager-console.  

-   Clientacties starten. Bijvoorbeeld, het clientbeleid downloaden als er een recente wijziging in de configuratie in de Configuration Manager-console is en u niet wachten wilt totdat de volgende tijdstip geplande.  

-   Handmatig een client toewijst aan een Configuration Manager-site of probeer een site te vinden. Vervolgens geeft u het achtervoegsel System DNS (Domain Name) voor beheerpunten die naar DNS publiceren.  

-   Configureer de clientcache die bestanden worden tijdelijk opgeslagen. Verwijder de bestanden in de cache als u meer schijfruimte voor het installeren van software vereist.  

-   Instellingen configureren voor clientbeheer via internet.  

-   Configuratiebasislijnen weergeven die op de client zijn geïmplementeerd, een conformiteitsevaluatie starten en conformiteitsrapporten weergeven.  
