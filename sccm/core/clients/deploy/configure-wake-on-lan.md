---
title: Wake on LAN configureren | Microsoft Docs
description: Selecteer Wake On LAN-instellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
caps.latest.revision: "7"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 9c920651ba1dc6e0a28df458d28956126ddbaff0
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>Het configureren van Wake on LAN in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Geef de Wake on LAN-instellingen voor System Center Configuration Manager als u computers uit de slaapstand wilt voor het installeren van vereiste software, zoals software-updates, toepassingen, takenreeksen en programma's te brengen.

U kunt de Wake on LAN aanvullen met behulp van de wake-up proxyclient-instellingen. Echter, voor het gebruik van wake-up proxy, moet u eerst Wake on LAN inschakelen voor de site en geef **alleen ontwaakpakketten gebruiken** en de **Unicast** optie voor de Wake on LAN-verzendingsmethode. Deze ontwaakoplossingen ondersteunt ook ad-hoc-verbindingen, zoals een verbinding met extern bureaublad.

Gebruik de eerste procedure voor het configureren van een primaire site voor Wake on LAN. Vervolgens gebruikt u de tweede procedure voor het configureren van de wake-up proxyclient-instellingen. Deze tweede procedure configureert u de standaardclientinstellingen voor de wake-up proxy-instellingen toepassen op alle computers in de hiërarchie. Als u deze instellingen wilt toepassen op alleen de geselecteerde computers, aangepaste apparaatinstellingen maken en toewijzen aan een verzameling waartoe de computers die u wilt configureren voor wake-up proxy. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-settings.md) voor meer informatie over het maken van aangepaste clientinstellingen.

Een computer die de wake-up proxy clientinstellingen ontvangt pauzeert waarschijnlijk de netwerkverbinding voor 1-3 seconden. Dit komt doordat de client opnieuw voor de netwerkkaart instellen moet zodat het stuurprogramma van de wake-up proxy erop.

> [!WARNING]
> Om te voorkomen onverwachte onderbreking van uw netwerkservices, moet u eerst wake-up proxy op een afgezonderde en representatieve netwerkinfrastructuur evalueren. Gebruik vervolgens aangepaste clientinstellingen uw test uitbreiden naar een selecte groep computers op verschillende subnetten. Zie voor meer informatie over wake-up proxy werkt [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

## <a name="to-configure-wake-on-lan-for-a-site"></a>Voor Wake on LAN voor een site configureren

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Sites**.
2. Klik op de primaire site om te configureren en klik vervolgens op **eigenschappen**.
3. Klik op de **Wake on LAN** tabblad en configureer de opties die u nodig voor deze site hebt. Ter ondersteuning van wake-up proxy, zorg ervoor dat u selecteert **alleen ontwaakpakketten gebruiken** en **Unicast**. Zie voor meer informatie [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).
4. Klik op **OK** en Herhaal de procedure voor alle primaire sites in de hiërarchie.

## <a name="to-configure-wake-up-proxy-client-settings"></a>Wake-up proxyclient-instellingen configureren

1. Ga in de Configuration Manager-console naar **beheer > clientinstellingen**.
2. Klik op **Standaardclientinstellingen**, en klik vervolgens op **eigenschappen**.
3. Selecteer **energiebeheer** en kies vervolgens **Ja** voor **wake-up proxy inschakelen**.
4. Bekijk en configureer zo nodig de andere wake-up proxy-instellingen. Zie voor meer informatie over deze instellingen [energiebeheerinstellingen](../../../core/clients/deploy/about-client-settings.md#power-management).
5. Klik op **OK** in het dialoogvenster sluiten en klik vervolgens op **OK** om de Standaardclientinstellingen dialoogvenster te sluiten.

De volgende Wake On LAN-rapporten kunt u de installatie en configuratie van wake-up proxy controleren:

- Samenvatting van implementatiestatus van Wake-up proxy
- Details van implementatiestatus van Wake-up proxy

> [!TIP]
> Als u wilt testen of wake-up proxy werkt, test u een verbinding met een computer in slaapstand. Bijvoorbeeld verbinding maken met een gedeelde map op die computer of probeer verbinding te maken met de computer met extern bureaublad. Als u directe toegang gebruikt, controleert u dat de IPv6-voorvoegsels werken door dezelfde tests uit voor een computer in slaapstand die zich momenteel op het Internet.
