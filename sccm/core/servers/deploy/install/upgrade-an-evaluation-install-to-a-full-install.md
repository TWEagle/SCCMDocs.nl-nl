---
title: "Evaluatie van de upgrade wordt geïnstalleerd"
titleSuffix: Configuration Manager
description: Ontdek hoe u een evaluatie-installatie bijwerken naar een volledige installatie van System Center Configuration Manager.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 942ac0a1d7681cb1efb06ff477a27a7c5c57654b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>Een evaluatie-installatie van System Center Configuration Manager bijwerken naar een volledige installatie

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u System Center Configuration Manager geïnstalleerd als een evaluatieversie na 180 dagen, de Configuration Manager-console, wordt alleen-lezen totdat u het product uit activeert de **siteonderhoud** pagina in het installatieprogramma. U hebt de optie voor een evaluatie-installatie bijwerken naar een volledige installatie op elk gewenst moment vóór of na de periode van 180 dagen.  

> [!NOTE]  
>  Wanneer u een Configuration Manager-console met een evaluatie-installatie van Configuration Manager verbindt, geeft de titelbalk van console het aantal dagen dat blijven totdat het evaluatie-installatie vervalt. Het aantal dagen wordt niet automatisch vernieuwd en wordt alleen bijgewerkt wanneer u een nieuwe verbinding met een site maken.  

 De volgende sites waarop een evaluatie-installatie wordt uitgevoerd, kunt u upgraden:  

-   Centrale beheersite  
-   Primaire site  

Omdat secundaire sites niet als evaluatie-installaties worden behandeld, hoeft u niet wijzigen van een secundaire site nadat de bovenliggende primaire site is bijgewerkt naar een volledige installatie.  

Vereisten voor de upgrade van een evaluatieversie naar een gelicentieerde versie:  

-   U moet een geldige productcode te gebruiken tijdens de upgrade hebben.  
-   Uw account moet hebben **beheerder** rechten op de computer waarop de site is geïnstalleerd.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>Een evaluatieversie van Configuration Manager bijwerken naar een gelicentieerde versie  

1.  Voer op de siteserver **Setup.exe** (het installatieprogramma van Configuration Manager) uit de installatiemap van Configuration Manager (**%path%\BIN\X64**). U kunt de kopie van Setup die bevindt op de siteserver in de map Configuration Manager, zich omdat siteonderhoudsopties niet beschikbaar zijn wanneer u Setup vanaf installatiemedia uitvoert moet uitvoeren.  
2.  Op de **voordat u begint** pagina **volgende**.  
3.  Op de **aan de slag** pagina **siteonderhoud uitvoeren of deze Site resetten**, en selecteer vervolgens **volgende**.  
4.  Op de **siteonderhoud** pagina **de evaluatieversie bijwerken naar een gelicentieerde versie**, voer een geldige productsleutel in en selecteer **volgende**.  
5.  Op de **licentievoorwaarden voor Microsoft-Software** pagina, lees en accepteer de licentievoorwaarden en selecteer vervolgens **volgende**.  
6.  Op de **configuratie** pagina **sluiten** om de wizard te voltooien.  

    > [!NOTE]  
    >  De titelbalk van een Configuration Manager-console die verbonden is met de site die u bijwerkt blijft kan aangeven dat de site nog steeds een evaluatieversie is totdat u de console en de site opnieuw verbinding maken.  
