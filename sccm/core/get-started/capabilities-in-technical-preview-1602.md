---
title: Mogelijkheden in Technical Preview 1602 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1602.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1602 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1602 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 Hier volgen nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_MDM"></a>Verbeteringen in mobile device management  

### <a name="ios-activation-lock"></a>iOS-Activeringsvergrendeling  
 System Center Configuration Manager kan u helpen bij het beheer van de activeringsvergrendeling voor iOS, een onderdeel van de app Zoek mijn iPhone voor apparaten met iOS 7.1 en hoger. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Nadat de vergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:  

-   Zoek mijn iPhone uitschakelen  

-   Het apparaat wissen  

-   Het apparaat opnieuw activeren  

 Configuration Manager kunnen aanvragen van de status van de Activeringsvergrendeling van apparaten voor zowel en zonder supervisie waarop iOS 7.1 en hoger wordt uitgevoerd. Voor apparaten onder supervisie kan met Intune de bypass-code van de activeringsvergrendeling worden opgehaald direct aan het apparaat worden uitgegeven.  

 Zie voor meer informatie [iOS-apparaten met Activeringsvergrendeling overslaan voor Configuration Manager-beschermen](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a>Verbeteringen aan Software Center in versie 1602  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>PC-computer en de gebruiker beleid vanuit Software Center vernieuwen  
 Een nieuwe optie **Synchronisatiebeleid** is toegevoegd aan de **opties** > **Computeronderhoud** pagina van het Software Center zorgt ervoor dat de PC vernieuwen van de Configuration Manager voor computer- en beleid.  

##  <a name="BKMK_Win10Servicing"></a>Verbeteringen in onderhoud van Windows 10  
 In de Technical Preview 1602 hebben we de volgende verbeteringen voor onderhoud van Windows 10 toegevoegd:  

-   Nieuwe filteropties voor onderhoudsplannen.  U kunt nu filteren op **taal**, **vereist**, en **titel**. Alleen de upgrades die voldoen aan de opgegeven criteria worden aan de gekoppelde implementatie toegevoegd.  

-   Wanneer u selecteert de **Upgrades** synchronisatie van classificatie voor software-updates, wordt er een waarschuwingsdialoogvenster weergegeven als u wilt laten u weten dat WSUS [hotfix 3095113](https://support.microsoft.com/kb/3095113) is vereist voor het synchroniseren van software-updates en voor het onderhoud van Windows 10 goed te laten werken.  In het dialoogvenster kunt u naar de knowledge base-artikel voor de hotfix gaan.  

-   Beschikbare Windows upgrades 10 worden nu alleen weergegeven in de **onderhoud van Windows 10** \ **alle Windows 10-Updates** knooppunt van de Configuration Manager-console. Deze updates worden niet meer weergegeven de **Software-Updates** \ **alle Software-Updates** knooppunt.  

-   Eindgebruikers die een Windows 10-upgradepakket starten wordt gevraagd een dialoogvenster waarmee ze weten dat ze hun besturingssysteem wordt bijgewerkt.  
