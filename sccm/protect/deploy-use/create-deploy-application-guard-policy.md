---
title: Een toepassing bescherming van Windows Defender-beleid maken en implementeren
titleSuffix: Configuration Manager
description: Maken en implementeren van beleid voor Windows Defender toepassing Guard.
ms.custom: na
ms.date: 11/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 
caps.latest.revision: "5"
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.openlocfilehash: db2508e5bbd1435fce432b6ef98d7968e68ea5ab
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="create-and-deploy-windows-defender-application-guard-policy----1351960---"></a>Windows Defender toepassing Guard beleid maken en implementeren<!-- 1351960 -->

U kunt maken en implementeren [Windows Defender toepassing Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) beleidsregels met behulp van de Configuration Manager endpoint protection. Deze beleidsregels kunt beveiligen van uw gebruikers via niet-vertrouwde websites in een beveiligde geïsoleerde container die is niet toegankelijk voor andere onderdelen van het besturingssysteem.

## <a name="prerequisites"></a>Vereisten

Maken en implementeren van een beleid voor Windows Defender toepassing Guard, moet u de Windows 10 vallen Creator Update. De Windows 10-apparaten waarop u het beleid implementeert moeten ook worden geconfigureerd met een beleid voor het isoleren van netwerken. Zie voor meer informatie de [overzicht van Windows Defender toepassing Guard](https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview). Deze functie werkt alleen met huidige Insider voor Windows 10-builds. Als u wilt testen, moeten uw clients worden uitgevoerd een recente Windows 10 Insider niet maken.


## <a name="create-a-policy-and-to-browse-the-available-settings"></a>Maak een beleid en de beschikbare instellingen bladeren:

1. Kies in de Configuration Manager-console **activa en naleving**.
2. In de **activa en naleving** werkruimte, kiest u **overzicht** > **Endpoint Protection** > **Windows Defender toepassing Guard**.
3. In de **Start** tabblad, in de **maken** groep, klikt u op **maken Windows Defender Guard toepassingsbeleid**.
4. Met behulp van de [blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97) als uitgangspunt, kunt u bladeren en de beschikbare instellingen configureren.
5. Op de **Netwerkdefinitie** pagina, geeft u de zakelijke identiteit en definieer de grens van uw bedrijfsnetwerk.

    > [!NOTE]
    > Windows 10-computers opslaan slechts één netwerk isolatie lijst op de client. U kunt twee soorten netwerk isolatie lijsten maken en implementeren naar de client:
    >
    >  - een van de Windows-gegevensbeveiliging
    >  - een van de Windows Defender toepassing Guard
    >
    > Als u beide beleidsregels implementeren, moeten deze netwerk isolatie lijsten overeenkomen. Als u lijsten die niet met dezelfde client overeenkomen implementeert, mislukt de implementatie. Zie voor meer informatie de [documentatie van Windows-gegevensbeveiliging](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).
    > 
    > 

6. Wanneer u klaar bent, voltooi de wizard en implementeer het beleid voor een of meer Windows 10-apparaten.

## <a name="next-steps"></a>Volgende stappen
Voor meer informatie over Windows Defender toepassing Guard, Zie [dit blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Zie ook voor meer informatie over Windows Defender toepassing Guard zelfstandige modus, [dit blogbericht](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).
