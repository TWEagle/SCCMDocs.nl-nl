---
title: Android-toepassingen maken | Microsoft Docs
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van toepassingen voor Android-apparaten.
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: "6"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3a89abc81cd70f4e499bf4e3087fd53915377c44
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Android-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft een of meer implementatietypen. Implementatietypen die bestaat uit de installatiebestanden en informatie die vereist is om software te implementeren op een apparaat. Een implementatietype heeft ook regels die specificeren hoe en wanneer de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De toepassing en implementatietype-typen automatisch maken door te lezen van de installatiebestanden van de toepassing.  
-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  
-   Een toepassing importeren uit een bestand.  

Zie [Start de wizard toepassing maken](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) voor de stappen die nodig zijn voor de Configuration Manager-toepassingen maken en implementatietypen. Houd er ook de volgende aandachtspunten in rekening wanneer u maken en implementeren van toepassingen voor Android-apparaten.  

## <a name="general-considerations-for-android-apps"></a>Algemene overwegingen voor Android-apps

Configuration Manager ondersteunt de implementatie van de volgende typen Apps voor Android:

|Apparaattype|Ondersteunde bestanden|
|-|-|
|Android|.APK|

De volgende implementatieacties worden ondersteund:

|Apparaattype|Ondersteunde bewerkingen|
|-|-|
|Android|**Beschikbare**, **vereist** de gebruiker moet toestemming geven om te installeren en verwijderen van zowel.|
|Android for Work | **Vereist** |

## <a name="approve-and-deploy-android-for-work-apps"></a>Goedkeuren en implementeren van Android voor bedrijfs-apps
Als een Configuration Manager-beheerder, kunt u ook apps in goedkeuren de [afspelen voor werk website](https://play.google.com/work), en deze apps implementeren op beheerde Android voor Work-apparaten.

Volg deze stappen apps in de Play voor werk store goedkeuren en implementeren voor beheerde Android voor werk apparaten ze naar de Configuration Manager-console synchroniseren. Om apps te werk gebruikersprofielen implementeert, moet u de apps in de Play for Work goedkeuren en vervolgens de apps met de Configuration Manager-console te synchroniseren.

1. Open een browser en Ga naar: https://play.google.com/work.
2. Meld u met behulp van de Google-beheerdersaccount dat u afhankelijk van uw Intune-tenant.
3. Voor apps die u wilt implementeren in uw omgeving en kies Bladeren **goedkeuren** voor elk van deze om de app beschikbaar maken voor Android for Work.
4. Ga in de Configuration Manager-console naar **beheerder** > **overzicht** > **Cloudservices** > **Android for Work** en kies **Sync**.
5. Wacht tot tien minuten om apps te synchroniseren en gaat u naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **licentiegegevens voor Store-Apps**.
6. Kies een app die vanuit Play for Work zijn gesynchroniseerd en kies vervolgens **toepassing maken**.
7. De wizard is voltooid en kies **sluiten**.
8. Ga naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**, kiest u een Android voor Work-app en gewoon implementeren.

Als u wilt synchroniseren Play voor zakelijke apps met Configuration Manager, moet u eerst ten minste één app in de Play voor werk website goedkeuren.
