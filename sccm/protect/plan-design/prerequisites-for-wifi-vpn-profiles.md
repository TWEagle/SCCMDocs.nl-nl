---
title: Wi-Fi en VPN-profiel vereisten | Microsoft-documenten
description: Meer informatie over de machtigingen die nodig zijn voor het beheren van certificaatprofielen, Wi-Fi-profielen en VPN-profielen in System Center Configuration Manager.
ms.custom: na
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
caps.latest.revision: 5
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31b68ede677df8b86412a334d1d100041a0e659e
ms.openlocfilehash: 309b0363f9b3ec4a31b8323b9e64c9f73060c281
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Vereisten voor Wi-Fi en VPN-profielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wi-Fi en VPN-profielen in System Center Configuration Manager bestaan alleen afhankelijkheden binnen het product.  

 U moet over de volgende beveiligingsmachtigingen beschikken om instellingen voor de toegang tot bedrijfsbronnen, zoals certificaatprofielen, Wi-Fi-profielen en VPN-profielen, te beheren:  

-   Weergeven en beheren van waarschuwingen en rapporten voor Wi-Fi- en -profielen: **Maak**, **verwijderen**, **wijzigen**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **waarschuwingen** object.  

-   Maken en beheren van certificaatprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **Certificaatprofiel** object.  

-   Wi-Fi-, certificaat- en VPN-mailprofielimplementaties beheren: **Configuratiebeleid toepassen**, **waarschuwing voor wijzigen clientstatus**, **lezen**, en **Resource lezen** voor de **verzameling** object.  

-   Alle configuratiebeleidsregels beheren: **Maak**, **verwijderen**, **wijzigen**, **lezen**, en **beveiligingsbereik instellen** voor de **configuratiebeleid** object.  

-   Query's uitvoeren die gerelateerd zijn aan Wi-Fi en VPN-profielen: **Lees** machtiging voor het **Query** object.  

-   Wi-Fi en VPN-profielgegevens in de System Center Configuration Manager-console weergeven: **Lees** machtiging voor het **Site** object.  

-   Statusberichten voor Wi-Fi en VPN-profielen weergeven: **Lees** machtiging voor het **statusberichten** object.  

-   Maken en aanpassen van het profiel voor vertrouwd CA-certificaat: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **profiel voor vertrouwd CA-certificaat** object.  

-   Maken en beheren van VPN-profielen: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **VPN-profiel** object.  

-   Maken en beheren van Wi-Fi-profielen: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **Wi-Fi-profiel** object.  

 De **toegang tot bedrijfsbronnen** beveiligingsrol bevat deze machtigingen die vereist zijn voor het beheren van Wi-Fi-profielen in System Center Configuration Manager. Zie [Beveiliging configureren in System Center Configuration Manager](../../core/plan-design/security/configure-security.md) voor meer informatie.

