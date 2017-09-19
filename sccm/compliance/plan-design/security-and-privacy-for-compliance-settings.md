---
title: Beveiliging en privacy voor compatibiliteitsinstellingen | Microsoft Docs
description: Meer informatie over de beveiliging aanbevolen procedures voor instellingen voor naleving in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: f38e03ffac6d3472bbef9c3b78e4c0e1f7cde598
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="security-and-privacy-for-compliance-settings-in-system-center-configuration-manager"></a>Beveiliging en privacy voor compatibiliteitsinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="security-best-practices-for-compliance-settings"></a>Aanbevolen beveiligingsprocedures voor nalevingsinstellingen  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Bewaak gevoelige gegevens niet.|Als u wilt voorkomen dat mogelijk gevoelige gegevens openbaar worden gemaakt, moet u configuratie-items niet zo configureren dat deze gegevens worden bewaakt.|  
|Configureer geen compatibiliteitsregels die gegevens gebruiken die door eindgebruikers kunnen worden gewijzigd.|Als u een nalevingsregel maakt op basis van gegevens die gebruikers kunnen wijzigen, zoals registerinstellingen voor configuratieopties, zijn de nalevingsresultaten niet betrouwbaar.|  
|Importeer Microsoft System Center-configuratiepakketten en andere configuratiegegevens alleen uit externe bronnen als deze beschikken over een geldige digitale handtekening van een vertrouwde uitgever.|Gepubliceerde configuratiegegevens kunnen digitaal worden ondertekend zodat u de uitgiftebron kunt verifiëren en er zeker van kunt zijn dat er niet is geknoeid met de gegevens. Als de verificatiecontrole van de digitale handtekening mislukt, ontvangt u een waarschuwing en wordt u gevraagd of u wilt doorgaan met importeren. Importeer geen niet-ondertekende gegevens als de bron en de integriteit van de gegevens niet kunnen worden geverifieerd.|  
|Toegangsbeheer implementeren om referentiecomputers te beveiligen.|Wanneer een gebruiker met beheerdersrechten een register- of bestandssysteeminstelling wil configureren door te bladeren naar een referentiecomputer, moet u ervoor zorgen dat er niet is geknoeid met de referentiecomputer.|  
|Beveilig het communicatiekanaal wanneer u naar een referentiecomputer bladert.|Gebruiken om te voorkomen dat knoeien met gegevens wanneer deze via het netwerk wordt overgedragen, Internet Protocol security (IPsec) of server message block (SMB) tussen de computer waarop de Configuration Manager-console en de referentiecomputer.|  
|Beperk en bewaak de gebruikers met beheerdersrechten die de rol van beheerder van nalevingsinstellingen krijgen|Gebruikers met beheerdersrechten die de rol **Beheerder van instellingen voor naleving** krijgen, kunnen configuratie-items voor alle apparaten en gebruikers in de hiërarchie implementeren. Configuratie-items kunnen zeer krachtig zijn en kunnen bijvoorbeeld scripts en registerconfiguraties bevatten.|  

## <a name="privacy-information-for-compliance-settings"></a>Privacygegevens voor nalevingsinstellingen  
 U kunt nalevingsinstellingen gebruiken om te evalueren of uw clientapparaten compliant zijn met configuratie-items die u in configuratiebasislijnen implementeert. Sommige instellingen kunnen automatisch worden hersteld als deze niet compliant zijn. De compatibiliteitsinformatie wordt door het beheerpunt naar de siteserver verzonden en opgeslagen in de sitedatabase. De informatie wordt versleuteld wanneer apparaten deze naar het beheerpunt verzenden, maar deze wordt niet in een versleutelde indeling opgeslagen in de sitedatabase. Informatie wordt bewaard in de database en wordt na negentig dagen verwijderd door de siteonderhoudstaak **Verouderde gegevens van Configuration Manager verwijderen** . U kunt het verwijderingsinterval configureren. Er wordt geen compatibiliteitsinformatie naar Microsoft verzonden.  

 Standaard worden nalevingsinstellingen niet door apparaten geëvalueerd. Bovendien moet u de configuratie-items en configuratiebasislijnen configureren en vervolgens implementeren voor apparaten.  
