---
title: Gebruik de Configuration Manager-client voor uitgebreide interoperabiliteit met de huidige vertakking | Microsoft Docs
description: Meer informatie over het gebruik van de client van de Long-Term Servicing Branch van Configuration Manager met een Current Branch-site.
ms.custom: na
ms.date: 08/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9772224be78eee2777137225a59b53b1fd77a627
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="use-the-configuration-manager-client-software-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>Gebruik de Configuration Manager-clientsoftware voor uitgebreide interoperabiliteit met toekomstige versies van een Current Branch-site

*Van toepassing op: System Center Configuration Manager (huidige vertakking), (op lange termijn onderhoud vertakking)*  

In sommige gevallen kan het bedrijfsbeleid mogelijk niet kunt u Configuration Manager-client op sommige computers regelmatig bij te werken. Bijvoorbeeld, mogelijk moet u voldoen aan de beleidsregels of het apparaat mogelijk bedrijfskritieke.

Terwijl u automatische Clientupgrade gebruikt indien mogelijk voor de meeste van uw clients, begint met Configuration Manager-update 1610 blijven moet, kunt u gebruikmaken van deze behoeften door een nieuwe client installeert voor langdurig gebruik, de uitgebreide interoperabiliteit-client (EIC) genoemd.

De EIC is compatibel met Configuration Manager-sites waarop versie 1610 of hoger. De EIC mag alleen worden gebruikt voor specifieke pc's die niet kunnen regelmatig, zoals een kiosk of verkooppuntapparaten bijgewerkt worden. De meest recente Configuration Manager-client gebruiken voor alle andere pc's.

## <a name="how-this-scenario-works"></a>De werking van dit scenario

Normaal gesproken wanneer u een nieuwe in de console-update voor de huidige vertakking installeert, clients automatisch hun clientsoftware bijwerken zodat ze deze nieuwe functies kunnen gebruiken.

Met dit scenario gebruikt u de huidige vertakking en ontvangen van de nieuwe functies en -updates. De meeste clients uitvoeren van de clientsoftware vanaf de huidige vertakking en die clientsoftware kunnen bijwerken met elke versie update die u installeert. Echter, in een subset van kritieke systemen die u niet wilt ontvangen van clientsoftware-updates u de uitgebreide interoperabiliteit client installeren. Deze clients Installeer geen nieuwe clientsoftware totdat u een nieuwe versie van de clientsoftware voor ze expliciet implementeren.

>[!IMPORTANT]
>De huidige vertakking site moet versie 1610 of hoger uitvoeren.

## <a name="how-to-use-the-eic"></a>Het gebruik van de EIC

1. De EIC (clientversie 5.00.8412) verkrijgen uit de map \SMSSETUP\Client van de installatiemedia van Configuration Manager 1606 update. Zorg ervoor dat u de volledige inhoud van de map kopieert.
2. De EIC handmatig installeren op deze apparaten. [Lees meer informatie over het handmatig installeren van de client](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).
3. Deze verzameling uitsluiten van clientupgrades.

>[!TIP]
>Als u in het Volume Licensing Service Center (VLSC) voor System Center Configuration Manager versie 1606 zoekt, gaat u naar de **downloadt en -sleutels** tabblad van de [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), zoek naar "system center-config" en selecteer vervolgens **System Center Config Mgr (huidige vertakking en LTSB)**.

## <a name="the-extended-interoperability-client-software"></a>De clientsoftware uitgebreide interoperabiliteit

De huidige EIC blijven worden ondersteund met de bijgewerkte versies van Configuration Manager Current Branch tot ten minste 18 November 2018. Controleer op deze pagina voor meer informatie over een nieuwe EIC of een uitbreiding van ondersteuning voor de bestaande EIC na deze tijd.

>[!TIP]
>De EIC wordt ondersteund voor ten minste twee jaar na de datum van release (Zie [ondersteuning voor versies van System Center Configuration Manager huidige vertakking](/sccm/core/servers/manage/current-branch-versions-supported)). Bijvoorbeeld: ondersteuning voor de huidige EIC twee jaar na de release van 1610, namelijk 18 November 2018.

Plan het bijwerken van de uitgebreide interoperabiliteit-client op apparaten die u met de huidige vertakking voordat ondersteuning beheert voor de client is verlopen. Een nieuwe versie van de client downloaden van Microsoft en vervolgens bijgewerkte clientsoftware implementeren op uw apparaten die gebruikmaken van de huidige uitgebreide interoperabiliteit client om dit te doen.

## <a name="limitations-of-the-extended-interoperability-client"></a>Beperkingen van de uitgebreide interoperabiliteit-client

- Updates voor de uitgebreide interoperabiliteit clientsoftware zijn niet beschikbaar met behulp van updates in de console. Aanvullende informatie voor het implementeren van een bijgewerkte clientsoftware worden opgegeven wanneer er een bijgewerkte client wordt uitgebracht.
- De EIC ondersteunt alleen software-updates, inventaris, en pakketten en programma's.

## <a name="next-steps"></a>Volgende stappen

Gebruik de informatie in [clients controleren](/sccm/core/clients/manage/monitor-clients) om ervoor te zorgen dat clients correct zijn geïnstalleerd op de gewenste apparaten.
