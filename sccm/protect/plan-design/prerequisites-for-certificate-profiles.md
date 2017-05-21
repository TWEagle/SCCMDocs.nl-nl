---
title: Profiel vereisten van het certificaat | Microsoft-documenten
description: Meer informatie over certificaatprofielen in System Center Configuration Manager en hun externe afhankelijkheden en afhankelijkheden binnen het product.
ms.custom: na
ms.date: 03/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0317fd02-3721-4634-b18b-7c976a4e92bf
caps.latest.revision: 9
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: fba52ee305fe67418f2fe544bfe94d10467236d0
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-certificate-profiles-in-system-center-configuration-manager"></a>Vereisten voor certificaatprofielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Certificaatprofielen in System Center Configuration Manager hebben externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Een uitgevende bedrijfscertificeringsinstantie met Active Directory Certificate Services (AD CS).<br /><br /> Certificaten kunnen alleen worden ingetrokken wanneer het computeraccount van de bovenste siteserver in de hiërarchie beschikt over rechten van *Certificaten verlenen en beheren* voor elke certificaatsjabloon die wordt gebruikt door een certificaatprofiel in Configuration Manager. U kunt echter ook certificaatbeheerdersmachtigingen verlenen voor alle certificaatsjablonen die door de CA worden gebruikt<br /><br /> Managergoedkeuring voor certificaataanvragen wordt ondersteund. De certificaatsjablonen die worden gebruikt om certificaten te verlenen moeten echter worden geconfigureerd voor **met de aanvraag meeleveren** voor het certificaatonderwerp, zodat deze waarde automatisch kan worden meegeleverd door dat System Center Configuration Manager.|Raadpleeg de Windows Server-documentatie voor meer informatie over Active Directory Certificate Services.<br /><br /> Voor WindowsServer 2012: [Overzicht van Active Directory Certificate Services](http://go.microsoft.com/fwlink/p/?LinkId=286744)<br /><br /> Voor WindowsServer 2008: [Active Directory Certificate Services in WindowsServer 2008](http://go.microsoft.com/fwlink/p/?LinkId=115018)|  
|De rolservice Registratieservice voor netwerkapparaten voor Active Directory Certificate Services in Windows Server 2012 R2.<br /><br /> Daarnaast:<br /><br /> Andere poortnummers dan TCP 443 (voor HTTPS) of TCP 80 (voor HTTP) worden niet ondersteund voor de communicatie tussen de client en Registratieservice voor netwerkapparaten.<br /><br /> Registratieservice voor netwerkapparaten moet zich op een andere server bevinden dan de uitgevende certificeringsinstantie.|System Center Configuration Manager communiceert met de Network Device Enrollment Service in Windows Server 2012 R2 te genereren en te verifiëren Simple Certificate Enrollment Protocol (SCEP)-aanvragen.<br /><br /> Als u certificaten uitgeeft voor gebruikers of apparaten die verbinding maken via Internet, zoals mobiele apparaten die worden beheerd door Microsoft Intune, zijn deze apparaten toegang hebben tot de server waarop de Network Device Enrollment Service wordt uitgevoerd vanaf het Internet. Installeer de server bijvoorbeeld in een perimeternetwerk, dat ook wel DMZ (demilitarized zone) of gescreend subnet wordt genoemd.<br /><br /> Als u een firewall gebruikt tussen de server waarop Registratieservice voor netwerkapparaten wordt uitgevoerd en de server met de uitgevende certificeringsinstantie, moet u de firewall zo configureren dat het communicatieverkeer (DCOM) tussen de twee servers is toegestaan. Deze firewallvereiste geldt ook voor de server waarop de System Center Configuration Manager-siteserver en de uitgevende Certificeringsinstantie zodat System Center Configuration Manager certificaten kan intrekken.<br /><br /> Als de Network Device Enrollment Service is geconfigureerd om SSL te vereisen, is een best practice bij beveiliging om ervoor te zorgen dat verbindende apparaten toegang de certificaatintrekkingslijst (CRL tot) het servercertificaat te valideren.<br /><br /> Zie [Een beleidsmodule gebruiken met de registratieservice voor netwerkapparaten](http://go.microsoft.com/fwlink/p/?LinkId=328657)voor meer informatie over Registratieservice voor netwerkapparaten in Windows Server 2012 R2.|  
|Als op de server met de uitgevende certificeringsinstantie Windows Server 2008 R2 wordt uitgevoerd, vereist deze server een hotfix voor SCEP-verlengingsaanvragen.|Installeer de hotfix als deze nog niet is geïnstalleerd op de computer met de uitgevende instantie. Zie voor meer informatie artikel [2483564: Aanvraag voor certificaatvernieuwing voor een certificaat SCEP mislukt in Windows Server 2008 R2 als het certificaat wordt beheerd met behulp van NDES](http://go.microsoft.com/fwlink/?LinkId=311945) in de Microsoft Knowledge Base.|  
|Een PKI-clientverificatiecertificaat en geëxporteerd basiscertificaat van de certificeringsinstantie.|Dit certificaat verifieert de server waarop de Network Device Enrollment Service voor System Center Configuration Manager wordt uitgevoerd.<br /><br /> Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md) voor meer informatie.|  
|Ondersteunde besturingssystemen voor apparaten.|U kunt certificaatprofielen implementeren voor apparaten waarop iOS, Windows 8.1, Windows RT 8.1, Windows 10 of Android wordt uitgevoerd.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Sitesysteemrol Certificaatregistratiepunt|Voordat u certificaatprofielen kunt gebruiken, moet u de sitesysteemrol Certificaatregistratiepunt installeren. Deze rol communiceert met de System Center Configuration Manager-database, de System Center Configuration Manager-siteserver en de System Center Configuration Manager-beleidsmodule.<br /><br /> Zie voor meer informatie over systeemvereisten voor deze sitesysteemrol en waar u de rol installeert in de hiërarchie, de **Sitesysteemvereisten** sectie het [ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md) onderwerp.<br /><br /> Houd er rekening mee dat het certificaatregistratiepunt niet mag worden geïnstalleerd op de server waarop ook de registratieservice voor netwerkapparaten wordt uitgevoerd.|  
|System Center Configuration Manager-beleidsmodule die is geïnstalleerd op de server waarop de rolservice registratieservice voor Active Directory Certificate Services|Voor het implementeren van certificaatprofielen, moet u de System Center Configuration Manager-beleidsmodule installeren. U vindt deze beleidsmodule op het installatiemedium van System Center Configuration Manager.|  
|Detectiegegevens|Waarden voor het certificaatonderwerp en de alternatieve naam zijn opgegeven door System Center Configuration Manager en opgehaald uit gegevens die worden verzameld tijdens detecties:<br /><br /> Voor gebruikerscertificaten: Detectie Active Directory-gebruiker<br /><br /> Voor computercertificaten: Detectie van Active Directory-systemen en netwerkdetectie|  
|Specifieke beveiligingsmachtigingen voor het beheren van certificaatprofielen|U moet over de volgende beveiligingsmachtigingen beschikken om instellingen voor de toegang tot bedrijfsbronnen, zoals certificaatprofielen, Wi-Fi-profielen en VPN-profielen, te beheren:<br /><br /> Weergeven en beheren van waarschuwingen en rapporten voor certificaatprofielen: **Maak**, **verwijderen**, **wijzigen**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** voor de **waarschuwingen** object.<br /><br /> Maken en beheren van certificaatprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** voor de **Certificaatprofiel** object.<br /><br /> Wi-Fi-profielen, certificaat- en VPN-beheren implementaties: **Configuratiebeleid toepassen**, **waarschuwing voor wijzigen clientstatus**, **lezen**, en **Resource lezen** voor de **verzameling** object.<br /><br /> Alle configuratiebeleidsregels beheren: **Maak**, **verwijderen**, **wijzigen**, **lezen** en **beveiligingsbereik instellen** voor de **configuratiebeleid** object.<br /><br /> Query's met betrekking tot certificaatprofielen uitvoeren: **Lees** machtiging voor het **Query** object.<br /><br /> Certificaatprofielgegevens in de System Center Configuration Manager-console weergeven: **Lees** machtiging voor het **Site** object.<br /><br /> Statusberichten voor certificaatprofielen weergeven: **Lees** machtiging voor het **statusberichten** object.<br /><br /> Maken en aanpassen van het profiel voor vertrouwd CA-certificaat: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** voor de **profiel voor vertrouwd CA-certificaat** object.<br /><br /> Maken en beheren van VPN-profielen: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** voor de **VPN-profiel** object.<br /><br /> Maken en beheren van Wi-Fi-profielen: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** voor de **Wi-Fi-profiel** object.<br /><br /> De **toegang tot bedrijfsbronnen** beveiligingsrol bevat deze machtigingen die vereist zijn voor het beheren van certificaatprofielen in System Center Configuration Manager. Zie de sectie **Beheer op basis van rollen configureren** in het onderwerp [Beveiliging configureren in System Center Configuration Manager](../../core/plan-design/security/configure-security.md) voor meer informatie.|  

