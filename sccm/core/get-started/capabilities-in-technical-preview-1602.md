---
title: Mogelijkheden in Technical Preview 1602 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1602.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1602 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1602 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_MDM"></a>Verbeteringen in beheer van mobiele apparaten  

### <a name="ios-activation-lock"></a>iOS Activeringsvergrendeling  
 System Center Configuration Manager kan u helpen bij het beheer van de activeringsvergrendeling voor iOS, een onderdeel van de app Zoek mijn iPhone voor apparaten met iOS 7.1 en hoger. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Nadat de vergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:  

-   Zoek mijn iPhone uitschakelen  

-   Het apparaat wissen  

-   Het apparaat opnieuw activeren  

 Configuration Manager kunnen de status van de Activeringsvergrendeling van supervisie en werkende apparaten met iOS 7.1 en hoger aanvragen. Voor apparaten onder supervisie kan met Intune de bypass-code van de activeringsvergrendeling worden opgehaald direct aan het apparaat worden uitgegeven.  

 Zie voor meer informatie, [bescherming van iOS-apparaten met Activeringsvergrendeling overslaan voor Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a>Verbeteringen in Software Center in versie 1602  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>PC-computer en de gebruiker beleid vanuit Software Center vernieuwen  
 Een nieuwe optie **Sync beleid** is toegevoegd aan de **opties** > **Computeronderhoud** pagina van het Software Center die ervoor zorgt dat de PC te vernieuwen van de Configuration Manager voor computer- en beleid.  

##  <a name="BKMK_Win10Servicing"></a>Verbeteringen voor het onderhoud van Windows 10  
 In de 1602 Technical Preview hebben we de volgende verbeteringen voor het onderhoud van Windows 10 toegevoegd:  

-   Nieuwe filteropties voor onderhoud plannen.  Nu kunt u filteren op **taal**, **vereist**, en **titel**. Alleen de upgrades die voldoen aan de opgegeven criteria worden aan de gekoppelde implementatie toegevoegd.  

-   Wanneer u selecteert de **Upgrades** synchronisatie classificatie voor software-updates, verschijnt een waarschuwingsdialoogvenster zodat u weet dat WSUS [hotfix 3095113](https://support.microsoft.com/kb/3095113) met succes softwareupdates te synchroniseren is vereist en voor Windows 10 onderhoud goed te laten werken.  In het dialoogvenster gaat u naar de knowledge base-artikel voor de hotfix.  

-   Beschikbare Windows 10 werkt nu alleen worden weergegeven in de **Windows 10 onderhoud** \ **alle Windows 10-Updates** knooppunt van de Configuration Manager-console. Deze updates niet meer weergegeven de **Software-Updates** \ **alle Software-Updates** knooppunt.  

-   Eindgebruikers die een Upgrade van Windows 10 pakket starten gevraagd een dialoogvenster waarmee ze weten dat ze hun besturingssysteem wordt bijgewerkt.  

