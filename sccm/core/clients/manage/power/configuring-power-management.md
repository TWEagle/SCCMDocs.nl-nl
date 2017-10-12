---
title: Energiebeheer configureren | Microsoft Docs
description: Energiebeheer in System Center Configuration Manager instellen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 7d2125464103cf0c040592c9f7ddbc25ae022758
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="configuring-power-management-in-system-center-configuration-manager"></a>Energiebeheer in System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Energiebeheer in System Center Configuration Manager gebruiken kunt, moet u de volgende configuratiestappen uitvoeren.  

## <a name="enable-and-configure-power-management-client-settings"></a>Energiebeheerinstellingen voor clients inschakelen en configureren  
 Met deze procedure configureert u de standaardinstellingen voor energiebeheer voor clients die voor alle computers in uw hiërarchie geldt. Als u wilt dat deze instellingen alleen van toepassing zijn op enkele computers, maakt u een aangepaste apparaatclientinstelling en wijst u deze toe aan een verzameling waartoe de computers behoren die u voor energiebeheer wilt gebruiken. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [het configureren van clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

#### <a name="to-enable-power-management-and-configure-client-settings"></a>Energiebeheer inschakelen en clientinstellingen configureren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Klik op **Clientinstellingen** in de werkruimte **Beheer**.  

3.  Klik op **Standaardclientinstellingen**.  

4.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

5.  Klik in het dialoogvenster **Standaardclientinstellingen** op **Energiebeheer**.  

6.  Configureer de volgende waarde voor de energiebeheerinstellingen voor clients:  

    -   **Energiebeheer van apparaten toestaan** : selecteer **Waar** in de vervolgkeuzelijst om energiebeheer in te schakelen.  

7.  Configureer de clientinstellingen die u nodig hebt. Zie voor een lijst met energiebeheerinstellingen voor clients die u kunt configureren, de [energiebeheer](../../../../core/clients/deploy/about-client-settings.md#power-management) sectie het [over clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) onderwerp.  

8.  Klik op **OK** om het dialoogvenster **Standaardclientinstellingen** te sluiten.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  

## <a name="exclude-computers-from-power-management"></a>Computers uitsluiten van energiebeheer  
 U kunt voorkomen dat verzamelingen computers energiebeheerinstellingen ontvangen. Als een computer lid is van een verzameling die is uitgesloten van instellingen voor energiebeheer, worden op die computer geen energiebeheerinstellingen toegepast, zelfs niet als de computer lid is van een andere verzameling waarop energiebeheerinstellingen van toepassing zijn.  

 U kunt computers om de volgende redenen uitsluiten van energiebeheer:  

-   Als er een zakelijke vereiste is om computers altijd ingeschakeld te hebben.  

-   Als u een controleverzameling computers hebt waarop u geen energiebeheerinstellingen wilt toepassen.  

-   Als u bepaalde computers hebt waarop geen energiebeheerinstellingen kunnen worden toegepast.  

-   Als u computers wilt uitsluiten waarop Windows Server met energiebeheer wordt uitgevoerd.  

> [!NOTE]  
>  Als de optie **Gebruikers toestaan hun apparaat uit te sluiten van energiebeheer** is geconfigureerd in de clientinstellingen, kunnen gebruikers hun eigen computers uitsluiten van energiebeheer via Software Center.  

 Als u wilt weten welke computers zijn uitgesloten van energiebeheer, voer dan het rapport **Uitgesloten Computers**uit. Zie voor meer informatie over dit rapport [uitgesloten Computers](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Excluded) in [bewaken en plannen voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  Energie-instellingen die worden toegepast op computers met Windows XP of Windows Server 2003 worden niet hersteld naar de oorspronkelijke waarden, zelfs niet als u de computer van energiebeheer uitsluit. In latere versies van Windows worden bij het uitsluiten van een computer voor energiebeheer alle energie-instellingen teruggezet naar de oorspronkelijke waarden. Het is niet mogelijk oorspronkelijke waarden van afzonderlijke energie-instellingen te herstellen.  

#### <a name="to-exclude-a-collection-of-computers-from-power-management"></a>Een verzameling computers uitsluiten van energiebeheer  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.  

3.  In de lijst **Apparaatverzamelingen** selecteert u de verzameling die u wilt uitsluiten van energiebeheer. Klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

4.  In de **energiebeheer** tabblad van de *< verzamelingsnaam\>***eigenschappen** dialoogvenster, **energiebeheerinstellingen nooit toepassen op computers in deze verzameling**.  

5.  Klik op **OK** sluiten de *< verzamelingsnaam\>***eigenschappen** in het dialoogvenster en uw instellingen op te slaan.  
