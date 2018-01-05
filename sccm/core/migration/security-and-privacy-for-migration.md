---
title: Migratie-beveiliging en privacy
titleSuffix: Configuration Manager
description: Aanbevolen beveiligingsprocedures en privacyinformatie voor migratie naar uw omgeving voor System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: "5"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 6c2fb0fe7ff3c126d1dcd70dd69103f9690f2938
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>Beveiliging en privacy voor migratie naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat aanbevolen beveiligingsprocedures en privacyinformatie voor migratie naar uw System Center Configuration Manager-omgeving.  

## <a name="security-best-practices-for-migration"></a>Aanbevolen beveiligingsprocedures voor migratie  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor migratie.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Gebruik het computeraccount voor de Account van de SMS-Provider voor de bron-siteserver en de SQL Server de Bronsiteaccount in plaats van een gebruikersaccount.|Als u een gebruikersaccount voor migratie gebruiken moet, verwijdert u de accountdetails als de migratie is voltooid.|  
|Gebruik IPsec wanneer u inhoud van een distributiepunt in een bronsite naar een distributiepunt op de bestemmingssite migreert.|Hoewel de gemigreerde inhoud wordt gehasht om te detecteren knoeien, als de gegevens worden gewijzigd terwijl ze worden overgedragen, mislukt de migratie.|  
|Beperk en bewaak de gebruikers met beheerdersrechten die migratietaken kunnen maken.|De integriteit van de database van de doelhiërarchie is afhankelijk van de integriteit van gegevens die de gebruiker met beheerdersrechten kiest voor het importeren van de bronhiërarchie. Bovendien kan deze gebruiker met beheerdersrechten alle gegevens lezen uit de bronhiërarchie.|  

### <a name="security-issues-for-migration"></a>Beveiligingsproblemen bij migratie  
Migratie heeft de volgende beveiligingsproblemen kijken:  

-   Clients die zijn geblokkeerd vanaf een bronsite mogelijk wel toegewezen aan de doelhiërarchie voordat de clientrecord wordt gemigreerd.  

     Hoewel de Configuration Manager de geblokkeerde status van clients die u migreert behoudt, de client wel worden toegewezen aan de doelhiërarchie als deze toerwijzing plaatsvindt voordat de migratie van de clientrecord is voltooid.  

-   Controleberichten worden niet gemigreerd.  

Als u gegevens van een bronsite naar een doelsite migreert, verliest u alle controle-informatie van de bronhiërarchie.  

## <a name="privacy-information-for-migration"></a>Privacyinformatie voor migratie  
 Migratie wordt informatie gedetecteerd van de sitedatabases die u in een broninfrastructuur identificeert en slaat deze gegevens naar de database in de doelhiërarchie. De informatie die door System Center Configuration Manager kan worden gedetecteerd via een bronsite of -hiërarchie, is afhankelijk van de functies die zijn ingeschakeld in de bronomgeving, evenals de beheerbewerkingen die zijn uitgevoerd in die bronomgeving.  

 Zie een van de volgende onderwerpen voor meer informatie over beveiliging en privacy-informatie:  

-   Zie voor meer informatie over de privacyinformatie voor Configuration Manager 2007 [beveiliging en Privacy voor Configuration Manager 2007](http://go.microsoft.com/fwlink/p/?LinkId=216450) in de Configuration Manager 2007-documentatiebibliotheek.  

-   Zie voor meer informatie over de privacy-informatie voor System Center 2012 Configuration Manager [beveiliging en Privacy voor System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682033.aspx) in de Documentatiebibliotheek van System Center 2012 Configuration Manager.  

-   Zie voor meer informatie over de privacyinformatie voor System Center Configuration Manager [beveiliging en privacy voor System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

U kunt enkele of alle ondersteunde gegevens migreren van een bronsite naar een doelhiërarchie.  

Migratie wordt niet standaard ingeschakeld en vereist verschillende configuratiestappen. Migratie-informatie is niet naar Microsoft verzonden.  

Bedenk wat uw privacyvereisten voordat u gegevens vanuit een bronhiërarchie migreert.  
