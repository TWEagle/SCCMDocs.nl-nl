---
title: Wake on LAN configureren | Microsoft-documenten
description: Selecteer Wake On LAN-instellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9c920651ba1dc6e0a28df458d28956126ddbaff0
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>Wake on LAN in System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Geef de Wake on LAN-instellingen voor System Center Configuration Manager wanneer u computers wilt halen uit de slaapstand vereiste software, zoals software-updates, toepassingen, takenreeksen en programma's te installeren.

U kunt Wake on LAN aanvullen door de wake-up proxyclient-instellingen. Echter wake-up proxy wilt gebruiken, moet u eerst Wake on LAN inschakelen voor de site en geef **alleen ontwaakpakketten gebruiken** en de **Unicast** optie voor het Wake op LAN-verzendingsmethode. Deze ontwaakoplossingen ondersteunt tevens ad-hocverbindingen, zoals een verbinding met extern bureaublad.

De eerste procedure gebruiken voor het configureren van een primaire site voor Wake on LAN. Vervolgens gebruikt u de tweede procedure de wake-up proxyclient-instellingen configureren. Met deze tweede procedure configureert u de standaardclientinstellingen voor de wake-up proxy-instellingen toepassen op alle computers in de hiërarchie. Als u deze instellingen wilt toepassen op alleen de geselecteerde computers, maakt u een aangepaste Apparaatinstelling en wijs deze toe aan een verzameling waartoe de computers die u voor wake-up proxy wilt configureren. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-settings.md) voor meer informatie over het maken van aangepaste clientinstellingen.

Een computer waarop de wake-up proxyclient-instellingen wordt waarschijnlijk de netwerkverbinding voor 1-3 seconden onderbroken. Dit komt doordat de client moet de netwerkinterfacekaart zodat het stuurprogramma voor wake-up proxy op het opnieuw.

> [!WARNING]
> Om te voorkomen onverwachte onderbreking van uw netwerkservices, eerst wake-up proxy beoordelen op een afgezonderde en representatieve netwerkinfrastructuur. Gebruik vervolgens aangepaste clientinstellingen moet worden uitgebreid van uw test in een geselecteerde groep computers op verschillende subnetten. Zie voor meer informatie over de werkwijze van wake-up proxy [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

## <a name="to-configure-wake-on-lan-for-a-site"></a>Wake on LAN voor een site configureren

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Sites**.
2. Klik op de primaire site om te configureren en klik vervolgens op **eigenschappen**.
3. Klik op de **Wake on LAN** tabblad en configureer de opties die u nodig voor deze site hebt. Zorg ervoor dat u selecteert voor het ondersteunen van wake-up proxy **alleen ontwaakpakketten gebruiken** en **Unicast**. Zie voor meer informatie [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).
4. Klik op **OK** en Herhaal de procedure voor alle primaire sites in de hiërarchie.

## <a name="to-configure-wake-up-proxy-client-settings"></a>Wake-up proxyclient-instellingen configureren

1. Ga in de Configuration Manager-console naar **beheer > clientinstellingen**.
2. Klik op **Standaardclientinstellingen**, en klik vervolgens op **eigenschappen**.
3. Selecteer **energiebeheer** en kies vervolgens **Ja** voor **wake-up proxy inschakelen**.
4. Bekijk en configureer, indien nodig de andere wake-up proxy-instellingen. Zie voor meer informatie over deze instellingen [energiebeheerinstellingen](../../../core/clients/deploy/about-client-settings.md#power-management).
5. Klik op **OK** in het dialoogvenster sluiten en klik vervolgens op **OK** om het dialoogvenster van de Standaardclientinstellingen te sluiten.

De volgende Wake On LAN-rapporten kunt u de installatie en configuratie van wake-up proxy controleren:

- Samenvatting van implementatiestatus van Wake-up proxy
- Details van implementatiestatus van Wake-up proxy

> [!TIP]
> Als u wilt testen of wake-up proxy werkt, test u een verbinding met een computer in slaapstand. Bijvoorbeeld, verbinding maken met een gedeelde map op die computer of probeer verbinding te maken met de computer via Extern bureaublad. Als u directe toegang, Controleer of de IPv6-voorvoegsels werken, door dezelfde tests uit op een computer in slaapstand die op het Internet.

