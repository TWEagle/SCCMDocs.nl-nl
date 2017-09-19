---
title: Monitor cloud management gateway - Configuratiebeheer | Microsoft Docs
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: fa58b55c2b99ce5c62226279499d8276b1216809
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor management cloudgateway in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610, nadat de cloud management gateway-service wordt uitgevoerd en de clients verbinding via dit maken, kunt u bewaken clients en netwerkverkeer om ervoor te zorgen dat u weet hoe de service wordt uitgevoerd.

## <a name="monitor-clients"></a>Monitor voor clients

Clients die zijn verbonden via de cloud management gateway-service wordt weergegeven in de Configuration Manager-console dezelfde manier lokale clients doen. Zie voor meer informatie [clients controleren](monitor-clients.md).

## <a name="monitor-traffic-in-the-console"></a>Verkeer van de monitor in de console

U kunt verkeer op cloud management gateway met de Configuration Manager-console controleren:

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Selecteer de cloud management gateway-service in het lijstdeelvenster.

3. De verkeersinformatie in het deelvenster met details voor de rol cloud management gateway-verbinding en de sitesysteemrollen waarmee die deze verbinding met maakt weergeven.

## <a name="set-up-outbound-traffic-alerts"></a>Uitgaand verkeer waarschuwingen instellen

Waarschuwingen voor uitgaand verkeer kunt u weten wanneer verkeer een drempelwaarde van 14 dagen (2 weken) nadert. Krijgt u de optie voor het instellen van verkeer waarschuwingen bij het maken van de cloud management gateway-service. Als u het gedeelte overgeslagen, kunt u nog steeds de waarschuwingen instellen nadat de service wordt uitgevoerd. En u kunt ook de instellingen voor meldingen op elk gewenst moment aanpassen.

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Met de rechtermuisknop op de cloud management gateway-service in het lijstdeelvenster en kies **eigenschappen**.

3. Klik op het tabblad waarschuwingen en kiest op (of uitschakelen) de drempel en de waarschuwingen. Geef vervolgens de 14 dagen drempelwaarde (in GB) en het percentage van de drempelwaarde voor het verhogen van de verschillende waarschuwingsniveaus.

4. Klik op **OK** wanneer u klaar bent.

## <a name="monitor-logs"></a>Logboeken van de monitor

De cloud management gateway-service genereert vermeldingen in een aantal logboekbestanden. Zie voor meer informatie [logboeken Configuration Manager](/sccm/core/plan-design/hierarchy/log-files).
