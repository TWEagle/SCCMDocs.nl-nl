---
title: Monitor cloud management gateway - Configuratiebeheer | Microsoft-documenten
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: daa0790995dc13ec2c78ae2d98a9eb38c0bcf8ae
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor cloud management gateway in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610, nadat de cloud management gateway-service wordt uitgevoerd en clients via deze verbinding maakt, kunt u controleren clients en netwerkverkeer om ervoor te zorgen dat u weet hoe de service wordt uitgevoerd.

## <a name="monitor-clients"></a>Monitor voor clients

Clients die verbonden zijn via de cloud management gateway-service worden weergegeven in de Configuration Manager-console dezelfde manier lokale clients doen. Zie voor meer informatie [clients bewaken](monitor-clients.md).

## <a name="monitor-traffic-in-the-console"></a>Verkeer van de monitor in de console

U kunt verkeer op cloud management gateway met de Configuration Manager-console controleren:

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Selecteer de cloud management gateway-service in het lijstdeelvenster.

3. Gegevens weergeven in het deelvenster details voor de rol cloud management gateway-verbinding en de clientcomputer met verbindt sitesysteemrollen.

## <a name="set-up-outbound-traffic-alerts"></a>Uitgaand verkeer waarschuwingen instellen

Uitgaand verkeer waarschuwingen te weten wanneer verkeer nadert een drempelwaarde 14 dagen (2 week). Krijgt u de optie voor het instellen van verkeer waarschuwingen bij het maken van de cloud management gateway-service. Als u deel overgeslagen, kunt u nog steeds de waarschuwingen instellen nadat de service wordt uitgevoerd. En u kunt ook de instellingen voor waarschuwingen op elk gewenst moment aanpassen.

1. Ga naar **beheer > Cloudservices > Management Gateway Cloud**.

2. Met de rechtermuisknop op de cloud management gateway-service in het lijstdeelvenster en kies **eigenschappen**.

3. Klik op het tabblad waarschuwingen en kies op (of uitschakelen) de drempel en waarschuwingen. Geef vervolgens de 14 dagen drempelwaarde (in GB) en het percentage van de drempelwaarde voor de verschillende waarschuwingsniveaus verhogen.

4. Klik op **OK** als u klaar bent.

## <a name="monitor-logs"></a>Monitor voor logboeken

De gatewayservice cloud management genereert vermeldingen in een aantal logboekbestanden. Zie voor meer informatie [Configuration Manager logs](/sccm/core/plan-design/hierarchy/log-files).

