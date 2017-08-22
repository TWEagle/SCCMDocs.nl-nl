---
title: Asset Intelligence beveiliging privacy | Microsoft Docs
description: Beveiliging en privacy-informatie ophalen voor Asset Intelligence in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0c6f7a0-dcae-4e6d-aa28-35d464d97ff7
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b12054cce52e2b83715a083d78a62e06b5127a2f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-asset-intelligence-in-system-center-configuration-manager"></a>Beveiliging en privacy voor Asset Intelligence in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor Asset Intelligence in System Center Configuration Manager.  

##  <a name="BKMK_Security_AI"></a> Best practices voor beveiliging voor Asset Intelligence  
 Pas de volgende best practices voor beveiliging toe wanneer u Asset Intelligence gebruikt.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Beveilig het bestands- en communicatiekanaal bij het importeren van een licentiebestand (Microsoft Volume Licensing of een Algemene licentieverklaring).|Gebruik machtigingen van het NTFS-bestandssysteem om ervoor te zorgen dat alleen gemachtigde gebruikers toegang kunnen krijgen tot de licentiebestanden en gebruik SMB-ondertekening (Server Message Block) om de integriteit van de gegevens te controleren wanneer deze worden overgebracht naar de siteserver tijdens het importeren.|  
|Gebruik het principe van minimale machtigingen om de licentiebestanden te importeren.|Gebruik rolgebaseerd beheer om de machtiging Asset Intelligence beheren te verlenen aan de gebruiker met beheerdersrechten die licentiebestanden importeert. De ingebouwde rol van Asset Intelligence omvat deze machtiging.|  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Privacy-informatie voor Asset Intelligence  
 Asset Intelligence breidt de inventarisatiefuncties van Configuration Manager naar een hoger niveau van asset-zichtbaarheid in de onderneming. De verzameling van Asset Intelligence-informatie is niet automatisch ingeschakeld. U kunt het type informatie dat door de hardware-inventaris wordt verzameld, wijzigen door rapportageklassen voor hardware-inventarisatie in te schakelen. Zie voor meer informatie [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Asset Intelligence-informatie wordt opgeslagen in de Configuration Manager-database op dezelfde manier als inventarisatie-informatie. Wanneer clients verbinding met beheerpunten maken met behulp van HTTPS, worden de gegevens altijd versleuteld tijdens de overdracht naar het beheerpunt. Wanneer clients verbinding maken met behulp van HTTP, kunt u configureren dat de gegevensoverdracht van inventarisatie wordt ondertekend en versleuteld. Inventarisatiegegevens worden niet in een versleutelde indeling in de database opgeslagen. Informatie wordt bewaard in de database en wordt na negentig dagen verwijderd door de siteonderhoudstaak **Verouderde inventarisgeschiedenis verwijderen** . U kunt het verwijderingsinterval configureren.  

 Asset Intelligence verzendt geen informatie over gebruikers en computers of licentiegebruik naar Microsoft. U kunt kiezen voor het verzenden van System Center Online aanvragen voor categorisatie, wat betekent dat u een of meer softwaretitels kunt coderen die niet-gecategoriseerd zijn en ze verzenden naar System Center Online voor onderzoek en categorisatie. Nadat een softwaretitel is geüpload, identificeren en categoriseren Microsoft-onderzoekers deze, en vervolgens wordt deze kennis beschikbaar voor alle klanten die de onlineservice gebruiken. U moet rekening houden met de volgende gevolgen voor de privacy bij het verzenden van gegevens naar System Center Online:  

-   Uploaden is alleen van toepassing op algemene informatie over de softwaretitel (naam, uitgever enzovoort) die u wilt verzenden naar System Center Online. Er wordt geen inventarisinformatie verzonden bij een upload.  

-   Het uploaden gebeurt nooit automatisch en het systeem is niet ontworpen om deze taak te automatiseren. U moet het uploaden van elke softwaretitel handmatig selecteren en goedkeuren.  

-   In een dialoogvenster ziet u precies welke gegevens worden geüpload voordat het uploadproces wordt gestart.  

-   Er worden geen licentiegegevens naar Microsoft verzonden. De licentie-informatie wordt opgeslagen in een apart gebied van de Configuration Manager-database en kan niet worden verzonden naar Microsoft.  

-   Een geüploade softwaretitel wordt openbaar, in de zin dat de kennis van deze bepaalde toepassing en haar categorisatie deel worden van de System Center Online Asset Intelligence-catalogus, en kan vervolgens worden gedownload naar andere gebruikers van de catalogus.  

-   De bron van de softwaretitel wordt niet vastgelegd in de Asset Intelligence-catalogus en wordt niet beschikbaar gesteld voor andere klanten. U moet echter nog steeds controleren dat u geen toepassingstitels laadt die persoonlijke informatie bevatten.  

-   Geüploade gegevens kunnen niet worden ingetrokken.  

 Neem kennis van de privacyverklaring van uw organisatie vóór u Asset Intelligence-gegevensverzameling configureert en beslist of informatie dient te worden verzonden naar System Center Online.  
