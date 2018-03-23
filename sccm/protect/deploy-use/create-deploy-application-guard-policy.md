---
title: Een toepassing bescherming van Windows Defender-beleid maken en implementeren
titleSuffix: System Center Configuration Manager
description: Maken en implementeren van beleid voor Windows Defender toepassing Guard.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ''
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: faa1a50b29fe4ba966812441243b81ee2d31b024
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Windows Defender toepassing Guard beleid maken en implementeren 
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*
<!-- 1351960 -->
U kunt maken en implementeren [Windows Defender toepassing Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) beleidsregels met behulp van de Configuration Manager endpoint protection. Deze beleidsregels kunt beveiligen van uw gebruikers via niet-vertrouwde websites in een beveiligde geïsoleerde container die is niet toegankelijk voor andere onderdelen van het besturingssysteem.

## <a name="prerequisites"></a>Vereisten

Als u wilt maken en implementeren van een beleid voor Windows Defender toepassing Guard, moet u de Windows 10 vallen Creator Update (1709). De Windows 10-apparaten waarop u het beleid implementeert moeten ook worden geconfigureerd met een beleid voor het isoleren van netwerken. Zie voor meer informatie de [overzicht van Windows Defender toepassing Guard](https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview). 


## <a name="create-a-policy-and-to-browse-the-available-settings"></a>Maak een beleid en de beschikbare instellingen bladeren:

1. Kies in de Configuration Manager-console **activa en naleving**.
2. In de **activa en naleving** werkruimte, kiest u **overzicht** > **Endpoint Protection** > **Windows Defender toepassing Guard**.
3. In de **Start** tabblad, in de **maken** groep, klikt u op **maken Windows Defender Guard toepassingsbeleid**.
4. Met behulp van de [artikel](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard) als uitgangspunt, kunt u bladeren en de beschikbare instellingen configureren. Configuration Manager kunt u om in te stellen bepaalde beleidsinstellingen Zie [interactie hostinstellingen](#BKMK_HIS) en [gedrag van toepassingen](#BKMK_AppB).
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

6. Wanneer u klaar bent, voltooi de wizard en implementeer het beleid voor een of meer apparaten met Windows 10 1709.

### <a name="bkmk_HIS"></a> Instellingen voor de interactie van de host
Hiermee configureert u interacties tussen de hostapparaten en de toepassing Guard-container. Voordat u Configuration Manager versie 1802, de interactie van beide toepassing gedrag en host zijn onder de **instellingen** tabblad.

- **Klembord** - onder instellingen voordat Configuration Manager 1802
    - Type inhoud toegestaan
        - Tekst
        - Installatiekopieën
- **Afdrukken:**
    - Afdrukken naar XPS inschakelen
    - Afdrukken naar PDF inschakelen
    - Afdrukken op printers lokale inschakelen
    - Afdrukken op netwerkprinters inschakelen
- **Afbeeldingen:** (te beginnen met Configuration Manager versie 1802)
    - Toegang tot Virtual graphics-processor
- **Bestanden:** (te beginnen met Configuration Manager versie 1802)
    - Gedownloade bestanden voor het hosten van opslaan

### <a name="bkmk_ABS"></a> Instellingen voor het gedrag van toepassing
Hiermee configureert u het gedrag van toepassingen in de toepassing Guard-sessie. Voordat u Configuration Manager versie 1802, de interactie van beide toepassing gedrag en host zijn onder de **instellingen** tabblad.

- **Inhoud:**
   - Enterprise-sites kunnen de inhoud buiten de onderneming, zoals invoegtoepassingen van derden laden.
- **Andere:**
    - De gebruiker gegenereerde browser gegevens bewaren
    - Beveiligingsgebeurtenissen in de geïsoleerde toepassing guard-sessie



## <a name="next-steps"></a>Volgende stappen
Voor meer informatie over Windows Defender toepassing Guard: [Overzicht van Windows Defender toepassing Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview).
[Windows Defender toepassing Guard Veelgestelde vragen over](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/faq-wd-app-guard).
