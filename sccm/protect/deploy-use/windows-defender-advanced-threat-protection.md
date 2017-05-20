---
title: Windows Defender geavanceerde dreigingen | Microsoft-documenten
description: Informatie over het beheren en controleren van de geavanceerde bedreiging bescherming van Windows Defender, een nieuwe service waarmee ondernemingen reageren op geavanceerde aanvallen.
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
caps.latest.revision: 5
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 237dc9cbccb973720a633490f096aed4bc16d183
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="windows-defender-advanced-threat-protection"></a>Windows Defender geavanceerde bedreiging beveiliging

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1606 van Configuration Manager (huidige vertakking), kunt Endpoint Protection beheren en controleren van Windows Defender geavanceerde bedreiging Protection (vrije. Windows Defender vrije is een nieuwe service waarmee ondernemingen om te detecteren, te onderzoeken en reageren op geavanceerde aanvallen op hun netwerken.  Meer informatie over [Windows Defender vrije](http://aka.ms/technet-wdatp). Configuration Manager-beleid kunnen u helpen voorbereiden en monitor beheerde Windows-10, versie 1607 (build 14328) of hoger.

Windows Defender vrije is een service in de [Windows Beveiligingscentrum](https://securitycenter.windows.com). Toe te voegen en implementeren van een client-voorbereiding-configuratiebestand, kunt Configuration Manager bewaken Implementatiestatus en de status van Windows Defender vrije-agent. Windows Defender vrije wordt alleen ondersteund op computers waarop de Configuration Manager-client wordt uitgevoerd. Beheer van mobiele apparaten op locatie en Intune hybride MDM-beheerde computers worden niet ondersteund.

 **Vereisten**  

-   Abonnement op de onlineservice Windows Defender geavanceerde bedreiging Protection  

-   Clients met Windows 10 1607 en hoger  

## <a name="how-to-create-an-onboarding-configuration-file"></a>Het maken van een configuratiebestand voorbereiden  

 1.  Meld u aan bij de [onlineservice Windows Defender vrije](https://securitycenter.windows.com/)   

 2.  Klik op de **eindpunt Management** menu-item.  

 3.  Selecteer **System Center Configuration Manager (huidige vertakking) versie 1606** en klikt u op **downloadpakket**.  

 4.  Download het bestand gecomprimeerd archief (.zip) en de inhoud te extraheren.

> [!IMPORTANT]
> Het configuratiebestand voor Windows Defender vrije bevat vertrouwelijke informatie die moet worden beveiligd.

## <a name="onboard-devices-for-windows-defender-atp"></a>Onboarding van apparaten voor Windows Defender vrije  

1.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **beleidsregels voor Windows Defender vrije** en klikt u op **Windows Defender vrije beleid maken**. De Wizard beleid voor Windows Defender vrije wordt geopend.  

2.  Type de **naam** en **beschrijving** voor het beleid voor Windows Defender vrije en selecteer **Onboarding**. Klik op **Volgende**.  

3.  **Bladeren** voor het configuratiebestand geleverd door uw organisatie Windows Defender vrije cloud service-tenant. Klik op **Volgende**.  

4.  Geef de voorbeeldbestanden die worden verzameld en gedeeld worden door beheerde apparaten voor analyse.  

    -   **Geen**   

    -   **Alle bestandstypen**  

     Klik op **Volgende**.  

5.  Bekijk het overzicht en voltooi de wizard.  

6.  U kunt nu het beleid voor Windows Defender vrije implementeren voor beheerde clientcomputers door te klikken op **implementeren**.  

## <a name="monitor-windows-defender-atp"></a>Monitor voor Windows Defender vrije  

1.  Navigeer in de Configuration Manager-console **bewaking** > **overzicht** > **beveiliging** en klik vervolgens op **Windows Defender vrije**.  

2.  Controleer het Windows Defender geavanceerde bedreiging Protection-dashboard.  

    -   **Windows Defender Agent Implementatiestatus** : het aantal en de hoeveelheid in aanmerking komende beheerde client-computers met actieve Windows Defender vrije beleid vrijgegeven  

    -   **Status van Windows Defender vrije Agent** – Percentage computerclients rapportage over de status voor hun Windows Defender vrije-agent  

        -   **Goede** -goed werkt  

        -   **Inactieve** -er zijn geen gegevens naar service worden verzonden tijdens periode  

        -   **De status van agent** -de service voor de agent in Windows wordt niet uitgevoerd  

        -   **Niet vrijgegeven** - beleid is toegepast, maar de agent niet vrijgeven beleid gemeld  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Het maken en implementeren van een configuratiebestand offboarding  

1.  Meld u aan bij de [onlineservice Windows Defender vrije](https://securitycenter.windows.com/)   

2.  Klik op de **eindpunt Management** menu-item.  

3.  Selecteer **System Center Configuration Manager (huidige vertakking) versie 1606** en klikt u op **eindpunt offboarding**.  

4.  Download het bestand gecomprimeerd archief (.zip) en de inhoud te extraheren. Offboarding bestanden zijn voor 30 dagen geldig.

5.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **beleidsregels voor Windows Defender vrije** en klikt u op **Windows Defender vrije beleid maken**. De Wizard beleid voor Windows Defender vrije wordt geopend.  

6.  Type de **naam** en **beschrijving** voor het beleid voor Windows Defender vrije en selecteer **Offboarding**. Klik op **Volgende**.  

7.  **Bladeren** voor het configuratiebestand geleverd door uw organisatie Windows Defender vrije cloud service-tenant. Klik op **Volgende**.  

8.  Bekijk het overzicht en voltooi de wizard.  

9.  U kunt nu het beleid voor Windows Defender vrije implementeren voor beheerde clientcomputers door te klikken op **implementeren**.  

> [!IMPORTANT]
> De configuratiebestanden voor Windows Defender vrije bevat vertrouwelijke informatie die moet worden beveiligd.

[Windows Defender geavanceerde bedreiging beveiliging](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Problemen met beveiliging van Windows Defender geavanceerde bedreiging voorbereiden](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)

