---
title: Endpoint Protection Client Help
titleSuffix: Configuration Manager
description: Meer informatie over de functies en verbeteringen in Endpoint Protection die beter te beschermen van uw computer tegen bedreigingen.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: "6"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 50b9e5c89776c57a5f1605d38f6fbbee7ecd833e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="endpoint-protection-client-help"></a>Endpoint Protection Client Help

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Deze versie van Windows Defender of Endpoint Protection bevat de volgende functies om uw computer te beschermen tegen bedreigingen:  

-   **Windows Firewall-integratie.** Tijdens de setup van Endpoint Protection kunt u Windows Firewall in- of uitschakelen.  
-   **Netwerkinspectiesysteem.** Deze functie verhoogt de real-timebeveiliging door netwerkverkeer te inspecteren om proactief te voorkomen dat misbruik wordt gemaakt van bekende beveiligingslekken in het netwerk.  
-   **Protection-engine.** Real-timebeveiliging zoekt en stopt schadelijke software geïnstalleerd of uitgevoerd op uw PC. De bijgewerkte engine biedt verbeterde detectie en opschoningsmogelijkheden met betere prestaties.  

Windows Defender wordt geleverd als onderdeel van het besturingssysteem Windows 10.  In eerdere versies van Windows kan de beheerder Windows Defender of Endpoint Protection met behulp van beheersoftware bieden.

U kunt ook een lijst met vinden [Veelgestelde vragen over Windows Defender- en Endpoint Protection](endpoint-protection-client-faq.md). Raadpleeg voor meer help [probleemoplossing Windows Defender of Endpoint Protection-client](troubleshoot-endpoint-client.md). Zie voor een lijst met nieuwe functies, [wat is er nieuwe Windows Defender-client](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## <a name="windows-firewall-integration"></a>Windows Firewall-integratie  
 Windows Firewall voorkomt dat aanvallers of schadelijke software toegang krijgen tot uw computer via internet of een netwerk. Wanneer u nu Endpoint Protection installeert, controleert de installatiewizard of Windows Firewall is ingeschakeld. Als u Windows Firewall met opzet hebt uitgeschakeld, kunt u voorkomen dat deze wordt ingeschakeld door een selectievakje te wissen. U kunt de Windows Firewall-instellingen op elk gewenst moment wijzigen via Systeem en beveiligingsinstellingen in het Configuratiescherm.  

## <a name="network-inspection-system"></a>Netwerkinspectiesysteem  
 Aanvallers voeren steeds vaker aanvallen via het netwerk uit op basis van blootgestelde beveiligingslekken voordat softwareleveranciers beveiligingsupdates kunnen ontwikkelen en distribueren. Onderzoek naar beveiligingslekken toont aan dat het een maand of langer kan duren vanaf de eerste melding van een aanval voordat een geschikte beveiligingsupdate is ontwikkeld, getest en vrijgegeven. Door dit gat in de beveiliging zijn veel computers gedurende lange tijd kwetsbaar voor aanvallen en misbruik. Netwerkinspectiesysteem werkt met real-timebeveiliging om u beter te beschermen tegen aanvallen vanuit het netwerk door de tijd tussen de detectie van een beveiligingslek en de implementatie van een update fors te verkorten van weken tot enkele uren.  

## <a name="award-winning-protection-engine"></a>Bekroonde beschermingsengine  
 Achter de schermen van Windows Defender of Endpoint Protection is de bekroonde beschermingsengine die regelmatig wordt bijgewerkt. De engine wordt ondersteund door een team van onderzoekers naar schadelijke software van het Microsoft Malware Protection Center, dat 24 uur per dag reageert op de nieuwste bedreigingen van schadelijke software.  

## <a name="windows-defender-settings"></a>Windows Defender-instellingen
Windows Defender-instellingen inschakelen-instellingen waarmee u uw computer beschermen tegen schadelijke software. Sommige Windows Defender-instellingen voor u kan worden beheerd door uw beheerder. U kunt andere met behulp van de Windows Defender-instellingen beheren. Het beste inschakelen van Windows Defender-instellingen om uw PC en gegevens te beveiligen.

Als u wilt weergeven van Windows Defender-instellingen, zoekt u `Windows Defender` op uw PC. Open **Windows Defender** en selecteer **instellingen**. Windows Defender-instellingen zijn:
- **Real-timebeveiliging** : zoeken en stoppen van schadelijke software geïnstalleerd of uitgevoerd op uw PC.
- **Cloud-gebaseerde beveiliging** -stuurt Windows Defender gegevens naar Microsoft over potentiële beveiligingsrisico's.
- **Automatische verzending van voorbeelden** -toestaan dat Windows Defender voorbeelden van verdachte bestanden verzenden naar Microsoft te verbeteren van de detectie van malware.
- **Uitsluitingen** -kunt u genoopt specifieke bestanden, mappen, bestandsextensies of processen van Windows Defender gescand.
- **Verbeterde melding** -Hiermee schakelt u meldingen die over de status van uw PC informeren. Zelfs **uit** u kritieke meldingen ontvangt.
- **Windows Defender Offline** -u kunt Windows Defender Offline om te zoeken en verwijderen van schadelijke software uitvoeren. Deze scan start opnieuw op uw PC en duurt ongeveer 15 minuten.

### <a name="see-also"></a>Zie tevens  
 [Veelgestelde vragen over de Endpoint Protection-client](endpoint-protection-client-faq.md)   
 [Problemen met Windows Defender of Endpoint Protection-client oplossen](troubleshoot-endpoint-client.md)
