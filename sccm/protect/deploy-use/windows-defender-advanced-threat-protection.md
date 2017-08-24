---
title: Windows Defender Advanced Threat Protection | Microsoft Docs
description: Informatie over het beheren en controleren van Windows Defender geavanceerde Threat Protection, een nieuwe service waarmee ondernemingen reageren op geavanceerde aanvallen.
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
caps.latest.revision: "5"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 6c3b67278fa587c137a29e174e277fb0f15872c8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1606 van Configuration Manager (huidige vertakking), kunt Endpoint Protection beheren en controleren van Windows Defender Advanced Threat Protection (ATP. Windows Defender ATP is een nieuwe service waarmee ondernemingen te detecteren, onderzoeken en reageren op geavanceerde aanvallen in hun netwerken.  Meer informatie over [Windows Defender ATP](http://aka.ms/technet-wdatp). Configuration Manager-beleid kunnen u helpen vrijgeven en monitor beheerd Windows 10 versie 1607 (build 14328) of hoger.

Windows Defender ATP is een service in de [Windows Beveiligingscentrum](https://securitycenter.windows.com). Configuration Manager kan door toe te voegen en een configuratiebestand voor de voorbereiding van client implementeren, bewaken Implementatiestatus en de status van Windows Defender ATP-agent. Windows Defender ATP wordt alleen ondersteund op computers met de Configuration Manager-client. Beheer van lokale mobiele apparaten en Intune hybride MDM-beheerde computers worden niet ondersteund.

 **Vereisten**  

-   Abonnement op de Windows Defender Advanced Threat Protection-onlineservice  
-   Clientcomputers met Windows 10 versie 1607 en hoger  
-   Clientcomputers waarop de Configuration Manager 1610 versie of hoger clientagent

## <a name="how-to-create-an-onboarding-configuration-file"></a>Het maken van een configuratiebestand voorbereiden  

 1.  Meld u aan bij de [Windows Defender ATP-onlineservice](https://securitycenter.windows.com/)   

 2.  Klik op de **eindpunt Management** menu-item.  

 3.  Selecteer **System Center Configuration Manager (huidige vertakking) versie 1606** en klik op **downloadpakket**.  

 4.  Download het bestand gecomprimeerd archief (.zip) en pak de inhoud.

> [!IMPORTANT]
> De Windows Defender ATP-configuratiebestand bevat gevoelige informatie die moet worden beveiligd.

## <a name="onboard-devices-for-windows-defender-atp"></a>Onboarding van apparaten voor Windows Defender ATP  

1.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **Windows Defender ATP-beleid** en klik op **Windows Defender ATP-beleid maken**. De Wizard Windows Defender ATP-beleid wordt geopend.  

2.  Typ de **naam** en **beschrijving** voor de Windows Defender ATP-beleid en selecteer **Onboarding**. Klik op **Volgende**.  

3.  **Blader** naar het configuratiebestand geleverd door Windows Defender ATP cloud service-tenant van uw organisatie. Klik op **Volgende**.  

4.  Geef de bestandsvoorbeelden die worden verzameld en gedeeld vanaf beheerde apparaten voor analyse.  

    -   **Geen**   

    -   **Alle bestandstypen**  

     Klik op **Volgende**.  

5.  Bekijk het overzicht en voltooi de wizard.  

6.  U kunt nu door te klikken op het Windows Defender ATP-beleid voor beheerde clientcomputers implementeren **implementeren**.  

## <a name="monitor-windows-defender-atp"></a>Monitor voor Windows Defender ATP  

1.  Navigeer in de Configuration Manager-console **bewaking** > **overzicht** > **beveiliging** en klik vervolgens op **Windows Defender ATP**.  

2.  Controleer het Windows Defender Advanced Threat Protection-dashboard.  

    -   **Implementatiestatus van Windows Defender Agent** : het aantal en het percentage van de in aanmerking komende beheerde clientcomputers met actieve vrijgegeven voor Windows Defender ATP-beleid  

    -   **Status van Windows Defender ATP-Agent** – Percentage computerclients rapportage over de status voor hun Windows Defender ATP-agent  

        -   **In orde** -goed werkt  

        -   **Inactieve** -er zijn geen gegevens verzonden naar service periode  

        -   **De status van agent** -de systeemservice voor de agent in Windows is niet actief  

        -   **Niet vrijgegeven** - beleid is toegepast, maar de agent geen beleid vrijgeven heeft gerapporteerd  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Het maken en implementeren van een configuratiebestand offboarding  

1.  Meld u aan bij de [Windows Defender ATP-onlineservice](https://securitycenter.windows.com/)   

2.  Klik op de **eindpunt Management** menu-item.  

3.  Selecteer **System Center Configuration Manager (huidige vertakking) versie 1606** en klik op **eindpunt offboarding**.  

4.  Download het bestand gecomprimeerd archief (.zip) en pak de inhoud. Offboarding-bestanden zijn voor 30 dagen geldig.

5.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **Windows Defender ATP-beleid** en klik op **Windows Defender ATP-beleid maken**. De Wizard Windows Defender ATP-beleid wordt geopend.  

6.  Typ de **naam** en **beschrijving** voor de Windows Defender ATP-beleid en selecteer **Offboarding**. Klik op **Volgende**.  

7.  **Blader** naar het configuratiebestand geleverd door Windows Defender ATP cloud service-tenant van uw organisatie. Klik op **Volgende**.  

8.  Bekijk het overzicht en voltooi de wizard.  

9.  U kunt nu door te klikken op het Windows Defender ATP-beleid voor beheerde clientcomputers implementeren **implementeren**.  

> [!IMPORTANT]
> De Windows Defender ATP-configuratiebestanden bevat vertrouwelijke informatie die moet worden beveiligd.

[Windows Defender Advanced Threat Protection](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Problemen met Windows Defender Advanced Threat Protection voorbereiden](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
