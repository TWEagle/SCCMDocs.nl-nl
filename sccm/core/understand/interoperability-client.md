---
title: Gebruik van de client van het uitgebreide interoperabiliteit met de huidige vertakking | Microsoft-documenten
description: Meer informatie over het gebruik van de client van de langetermijndoelen onderhoud vertakking van Configuration Manager met een vertakking van huidige site.
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: 0
author: robstackmsft
ms.author: robstack
Robots: NOINDEX,NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 4cc339e28110a3097c318b61224ae7692c47a31a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-client-software-from-the-version-1606-baseline-media-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>De clientsoftware van de versie 1606 basislijn media gebruiken voor uitgebreide interoperabiliteit met toekomstige versies van een site huidige vertakking

*Van toepassing op: System Center Configuration Manager (huidige vertakking) (op lange termijn onderhoud vertakking)*  

U kunt de Configuration Manager clientsoftware voor Windows-computers (client.msi) van de versie 1606 basislijn media DVD die u ontvangt met System Center 2016 of vanuit een of een versie van System Center Configuration Manager (huidige vertakking en langetermijnbeveiliging onderhoud vertakking 1606) voor het beheren van apparaten die deel uitmaken van een site huidige vertakking. Deze client wordt de client uitgebreide interoperabiliteit genoemd.

## <a name="how-this-scenario-works"></a>Hoe werkt dit scenario:
Normaal gesproken wanneer u een nieuwe console update voor de huidige vertakking installeert, clients automatisch hun clientsoftware bijwerken zodat ze deze nieuwe functies kunnen gebruiken.

Met dit scenario gebruikt u de huidige vertakking en de nieuwe functies en updates ontvangen. De meeste clients uitvoeren van de clientsoftware vanaf de huidige vertakking en die clientsoftware kunnen bijwerken met elke versie bijwerken die u installeert. Echter, in een subset van kritieke systemen die u niet wilt dat deze clientsoftware-updates ontvangen, u de uitgebreide interoperabiliteit client installeert. Deze clients wordt de nieuwe clientsoftware niet geïnstalleerd totdat u een nieuwe versie van de clientsoftware voor ze expliciet implementeren.

Meer informatie over het voorkomen dat huidige vertakking clients automatisch bijwerken wanneer u een nieuwe versie van Configuration Manager installeert, worden met huidige vertakking versie 1610.

Versie moet worden uitgevoerd in het huidige filiaal 1606 of hoger.

## <a name="the-extended-interoperability-client-software"></a>De clientsoftware uitgebreide interoperabiliteit
Als u de client uitgebreide interoperabiliteit van de System Center 2016 of release voor System Center Configuration Manager (huidige vertakking en langetermijnbeveiliging onderhoud vertakking 1606) met een vertakking van huidige site, wordt de client wordt ondersteund voor twee jaar na de algemene beschikbaarheid van de release van oktober 12de 2016.

Plan het bijwerken van de uitgebreide interoperabiliteit-client op apparaten die u met de huidige vertakking voordat ondersteuning beheert voor de client is verlopen. Om te doen zodat u een nieuwe versie van de client van Microsoft downloaden en dat bijgewerkte clientsoftware vervolgens implementeren op uw apparaten die gebruikmaken van de huidige uitgebreid interoperabiliteit client.

**De beperkingen van de client uitgebreide interoperabiliteit:**
-     Updates voor de clientsoftware uitgebreide interoperabiliteit zijn met behulp van de console updates niet beschikbaar. Aanvullende informatie voor het implementeren van een bijgewerkte clientsoftware wordt aangeboden wanneer een bijgewerkte client zijn vrijgegeven.

## <a name="identify-the-client-version-you-use"></a>De clientversie u identificeren
Hieronder staan de belangrijke clientversies beschikbaar voor het huidige vertakking en LTSB:

|Clientversie|Vertakking en versie |  
|----------------|---------------------|
|5.00.8325.xxxx |    -Huidige vertakking 1511|
|5.00.8355.xxxx    |-Huidige vertakking 1602|
|5.00.8412.1307    |-Huidige vertakking 1606 </br> -Huidige vertakking 1606 met het updatepakket 1606 hotfix (KB3186654)</br>-Uitgebreide interoperabiliteit client vanaf het medium versie 1606 basislijn|  

U kunt op de client de versie van de client weergeven op de **algemeen** tabblad van de Configuration Manager in het Configuratiescherm.

Op de **onderdelen** tabblad van het onderdeel sommige onderdelen verschillende waarden weergegeven. Voor een clientversie 8412.1307 kunnen bijvoorbeeld enkele onderdelen worden weergegeven als 5.00.8412. **1000** of 5.00.8412. **1006**.  Deze verschillen in de laatste vier cijfers voor sommige onderdelen is normaal en geeft niet aan een storing in het onderdeel bij te werken naar de huidige clientversie.

