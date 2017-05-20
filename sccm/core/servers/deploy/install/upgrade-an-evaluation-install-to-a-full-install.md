---
title: Evaluatie-installatie bijwerken | Microsoft-documenten
description: Leer hoe u een evaluatie-installatie bijwerken naar een volledige installatie van System Center Configuration Manager.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d1bf0fdc3e735eb31492476fd46f008620150c0b
ms.openlocfilehash: 8f951805c2fc25059965c15c94934c0f8546735c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>Een evaluatie-installatie van System Center Configuration Manager bijwerken naar een volledige installatie

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u System Center Configuration Manager geïnstalleerd als een evaluatieversie na verloop van 180 dagen, de Configuration Manager-console, wordt alleen-lezen totdat u het product uit activeert de **siteonderhoud** pagina in het installatieprogramma. U hebt de optie voor het upgraden van een evaluatie-installatie naar een volledige installatie op elk gewenst moment tijdens of na de periode van 180 dagen.  

> [!NOTE]  
>  Als u een Configuration Manager-console met een evaluatie-installatie van Configuration Manager verbindt, geeft de titelbalk van console het aantal dagen dat blijven totdat de evaluatie-installatie vervalt. Het aantal dagen wordt niet automatisch vernieuwd en wordt alleen bijgewerkt wanneer u een nieuwe verbinding met een site maken.  

 U kunt de volgende sites met een evaluatie-installatie bijwerken:  

-   Centrale beheersite  
-   Primaire site  

Omdat secundaire sites niet als evaluatie-installaties worden behandeld, hoeft u niet te wijzigen van een secundaire site nadat de primaire bovenliggende site is bijgewerkt naar een volledige installatie.  

Vereisten voor een evaluatieversie bijwerken naar een versie met licentie:  

-   U moet een geldige productsleutel moet worden gebruikt tijdens de upgrade hebben.  
-   Uw account moet beschikken over **Administrator** rechten op de computer waarop de site is geïnstalleerd.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>Een evaluatieversie van Configuration Manager bijwerken naar een versie met licentie  

1.  Voer op de siteserver **Setup.exe** (installatie van Configuration Manager) uit de installatiemap van Configuration Manager (**%path%\BIN\X64**). U kunt de kopie van Setup met een locatie op de siteserver in de map Configuration Manager omdat opties voor siteonderhoud niet beschikbaar zijn wanneer u Setup vanaf installatiemedia uitvoert moet uitvoeren.  
2.  Op de **voordat u begint** optie **volgende**.  
3.  Op de **aan de slag** optie **siteonderhoud uitvoeren of deze Site resetten**, en selecteer vervolgens **volgende**.  
4.  Op de **siteonderhoud** optie **de evaluatieversie bijwerken naar een gelicentieerde editie**, voer een geldige productsleutel in en selecteer **volgende**.  
5.  Op de **licentievoorwaarden voor Microsoft-Software** pagina lees en accepteer de licentievoorwaarden en selecteer vervolgens **volgende**.  
6.  Op de **configuratie** optie **sluiten** om de wizard te voltooien.  

    > [!NOTE]  
    >  De titelbalk van een Configuration Manager-console die verbonden zijn met de site die u een upgrade blijft geeft aan dat de site nog steeds een evaluatieversie totdat u de console en de site opnieuw.  

