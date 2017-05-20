---
title: Endpoint Protection Client Help | Microsoft-documenten
description: Meer informatie over functies en verbeteringen in de Endpoint Protection waarmee beter beveiligen van uw computer tegen bedreigingen.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: 6
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 212c73fcb947c3b56da6055bf47fe078301ad90d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection-client-help"></a>Endpoint Protection Client Help

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Deze versie van Windows Defender of Endpoint Protection omvat de volgende functies om uw computer beschermen tegen bedreigingen:  

-   **Windows Firewall-integratie.** Tijdens de setup van Endpoint Protection kunt u Windows Firewall in- of uitschakelen.  
-   **Netwerkinspectiesysteem.** Deze functie verhoogt de real-timebeveiliging door netwerkverkeer te inspecteren om proactief te voorkomen dat misbruik wordt gemaakt van bekende beveiligingslekken in het netwerk.  
-   **Protection-engine.** Real-timebeveiliging zoekt en stopt de schadelijke software installeren of uitvoeren op uw PC. De bijgewerkte engine biedt verbeterde detectie en opschoningsmogelijkheden met betere prestaties.  

Windows Defender wordt geleverd als onderdeel van het besturingssysteem Windows 10.  In eerdere versies van Windows kan uw beheerder Windows Defender of Endpoint Protection met behulp van beheersoftware geeft.

U vindt ook een lijst met [Veelgestelde vragen voor Windows Defender en Endpoint Protection](endpoint-protection-client-faq.md). Raadpleeg voor meer help [Windows Defender probleemoplossing of Endpoint Protection client](troubleshoot-endpoint-client.md). Zie voor een lijst met nieuwe functies, [wat nieuwe Windows Defender-client is](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender).

## <a name="windows-firewall-integration"></a>Windows Firewall-integratie  
 Windows Firewall voorkomt dat aanvallers of schadelijke software toegang krijgen tot uw computer via internet of een netwerk. Wanneer u nu Endpoint Protection installeert, controleert de installatiewizard of Windows Firewall is ingeschakeld. Als u Windows Firewall met opzet hebt uitgeschakeld, kunt u voorkomen dat deze wordt ingeschakeld door een selectievakje te wissen. U kunt de Windows Firewall-instellingen op elk gewenst moment wijzigen via Systeem en beveiligingsinstellingen in het Configuratiescherm.  

## <a name="network-inspection-system"></a>Netwerkinspectiesysteem  
 Aanvallers voeren steeds vaker aanvallen via het netwerk uit op basis van blootgestelde beveiligingslekken voordat softwareleveranciers beveiligingsupdates kunnen ontwikkelen en distribueren. Onderzoek naar beveiligingslekken toont aan dat het een maand of langer kan duren vanaf de eerste melding van een aanval voordat een geschikte beveiligingsupdate is ontwikkeld, getest en vrijgegeven. Door dit gat in de beveiliging zijn veel computers gedurende lange tijd kwetsbaar voor aanvallen en misbruik. Netwerkinspectiesysteem werkt met real-timebeveiliging om u beter te beschermen tegen aanvallen vanuit het netwerk door de tijd tussen de detectie van een beveiligingslek en de implementatie van een update fors te verkorten van weken tot enkele uren.  

## <a name="award-winning-protection-engine"></a>Bekroonde beschermingsengine  
 Achter de schermen van Windows Defender of Endpoint Protection is de bekroonde protection-engine die wordt regelmatig bijgewerkt. De engine wordt ondersteund door een team van onderzoekers naar schadelijke software van het Microsoft Malware Protection Center, dat 24 uur per dag reageert op de nieuwste bedreigingen van schadelijke software.  

## <a name="windows-defender-settings"></a>Windows Defender-instellingen
Windows Defender-instellingen kunnen instellingen waarmee u uw PC te beveiligen tegen kwaadaardige software. De beheerder kan sommige Windows Defender instellingen beheren voor u. U kunt andere met behulp van Windows Defender-instellingen beheren. U wordt aangeraden dat u Windows Defender instellingen inschakelen om te helpen beveiligen van uw PC en gegevens.

Windows Defender als instellingen wilt weergeven, zoekt u naar `Windows Defender` op uw PC. Open **Windows Defender** en selecteer **instellingen**. Instellingen voor Windows Defender zijn:
- **Real-timebeveiliging** : zoeken en stoppen van schadelijke software installeren of uitvoeren op uw PC.
- **Cloud-gebaseerde beveiliging** -Windows Defender verzendt gegevens naar Microsoft over de mogelijke bedreigingen.
- **Automatische verzending van voorbeelden** -toestaan Windows Defender voorbeelden van verdachte bestanden verzenden naar Microsoft te helpen verbeteren van de detectie van malware.
- **Uitsluitingen** -u kunt genoopt specifieke bestanden, mappen, bestandsextensies of processen van Windows Defender gescand.
- **Verbeterde melding** -Hiermee schakelt u meldingen waarmee u wordt geïnformeerd over de status van uw PC. Zelfs **uit** u kritieke meldingen ontvangt.
- **Windows Defender Offline** -u kunt Windows Defender Offline om te zoeken en verwijderen van schadelijke software uitvoeren. Deze scan uw PC opnieuw wordt gestart en wordt over 15 minuten duren.

### <a name="see-also"></a>Zie tevens  
 [Veelgestelde vragen over de Endpoint Protection-client](endpoint-protection-client-faq.md)   
 [Windows Defender of Endpoint Protection-client oplossen](troubleshoot-endpoint-client.md)

