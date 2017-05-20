---
title: Android-toepassingen maken | Microsoft-documenten
description: Zie welke overwegingen die u moet ondernemen in rekening wanneer u toepassingen maken en voor Android-apparaten implementeren.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: d3b20a59a9147e09e58f04f83f97fd72ebfef5a1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Android-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft een of meer implementatietypen die deel uitmaken van de installatiebestanden en informatie die nodig zijn voor het implementeren van software voor een apparaat. Een implementatietype bevat ook regels die specificeren waar en hoe de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De implementatie van toepassingen en -typen automatisch maken via het lezen van de installatiebestanden van de toepassing.  
-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  
-   Een toepassing importeren uit een bestand.  

Zie [Start de wizard toepassing](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) voor de stappen die nodig zijn voor create Configuration Manager-toepassingen en implementatietypen. Houd ook rekening met het volgende in gedachten wanneer u toepassingen maken en voor Android-apparaten implementeren.  

## <a name="general-considerations-for-android-apps"></a>Algemene overwegingen voor Android-apps

Configuration Manager ondersteunt de implementatie van de volgende typen van de app voor Android:

|Apparaattype|Ondersteunde bestanden|
|-|-|
|Android|.APK|

De volgende implementatieacties worden ondersteund:

|Apparaattype|Ondersteunde bewerkingen|
|-|-|
|Android|**Beschikbare**, **vereist**. De gebruiker moet toestemming geven om te installeren en verwijderen.

## <a name="approve-and-deploy-android-for-work-apps"></a>Goedkeuren en implementeren van Android voor zakelijke apps
Als een Configuration Manager-beheerder, kunt u ook goedkeuren en implementeren van apps in de [afspelen voor werk website](https://play.google.com/work), en deze apps implementeren op beheerde Android voor werk apparaten.

Volg deze stappen voor het goedkeuren van apps in de Play voor werk store, ze te synchroniseren met de Configuration Manager-console en deze beheerde Android voor werk apparaten implementeren. Voor apps op werk gebruikersprofielen implementeert, moet u de apps in Play for Work goedkeuren en vervolgens de apps met de Configuration Manager-console te synchroniseren.

1. Open een browser en Ga naar: https://play.google.com/work.
2. Meld u aan met behulp van de Google-beheeraccount die u aan uw Intune-tenant gekoppeld.
3. Bladeren naar apps die u wilt implementeren in uw omgeving en kies **goedkeuren** voor elk van deze om de app beschikbaar maken voor Android voor werk.
4. Ga in de Configuration Manager-console naar **Administrator** > **overzicht** > **Cloudservices** > **Android for Work** en kies **Sync**.
5. Wacht tot tien minuten om apps te synchroniseren en ga vervolgens naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **licentie-informatie voor de Store-Apps**.
6. Kies een app van Play voor taken die zijn gesynchroniseerd en kies **toepassing maken**.
7. De wizard hebt voltooid en kies **sluiten**.
8. Ga naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**, kiest u een Android voor werk app en gewoon implementeren.

Als u wilt synchroniseren Play voor zakelijke apps met Configuration Manager, moet u ten minste één app in de Play voor werk website eerst goedkeuren.

