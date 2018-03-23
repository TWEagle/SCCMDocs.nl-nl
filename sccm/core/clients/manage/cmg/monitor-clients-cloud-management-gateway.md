---
title: Monitor cloud management gateway
titleSuffix: Configuration Manager
description: Clients en netwerkverkeer via de cloud management gateway (CMG) bewaken.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18a98ae924b985b08aed911797b07ef0a1974420
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor management cloudgateway in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat de cloud management gateway wordt uitgevoerd en de clients verbinding via dit maken, kunt u bewaken clients en netwerkverkeer om ervoor te zorgen dat u weet hoe de service wordt uitgevoerd.



## <a name="monitor-clients"></a>Monitor voor clients

Clients die zijn verbonden via de cloud management gateway wordt weergegeven in de Configuration Manager-console dezelfde manier lokale clients doen. Zie voor meer informatie [clients controleren](/sccm/core/clients/manage/monitor-clients).



## <a name="monitor-traffic-in-the-console"></a>Verkeer van de monitor in de console

Monitor voor verkeer op de cloud management gateway met de Configuration Manager-console:

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Selecteer de cloud-management-gateway in het lijstdeelvenster.

3. De verkeersinformatie in het deelvenster met details voor het cloudverbindingspunt management gateway en de sitesysteemrollen waarmee die deze verbinding met maakt weergeven.



## <a name="set-up-outbound-traffic-alerts"></a>Uitgaand verkeer waarschuwingen instellen

Uitgaand verkeer waarschuwingen helpen u weten wanneer netwerkverkeer een drempelwaarde 14 dagen nadert. Wanneer u de cloud management gateway maakt, kunt u verkeer waarschuwingen instellen. Als u het gedeelte overgeslagen, kunt u nog steeds de waarschuwingen instellen nadat de service wordt uitgevoerd. De instellingen voor meldingen op elk gewenst moment aanpassen.

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Met de rechtermuisknop op de cloud-management-gateway in het lijstdeelvenster en kies **eigenschappen**.

3. Klik op de **waarschuwingen** tabblad. Schakel de drempel en de waarschuwingen. Geef de drempelwaarde 14 dagen voor gegevens in gigabytes (GB). Ook Geef het drempelwaardepercentage voor de verschillende waarschuwingsniveaus verhogen.

4. Klik op **OK** wanneer u klaar bent.



## <a name="monitor-logs"></a>Logboeken van de monitor

De cloud management gateway vermeldingen in een aantal logboekbestanden genereert. Zie voor meer informatie [logboeken Configuration Manager](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).
