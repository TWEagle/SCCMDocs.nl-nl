---
title: Intune-abonnement instellen | Microsoft Docs
description: Stel een Intune-abonnement om licenties voor On-premises Mobile Device Management in System Center Configuration Manager te volgen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 5a81ec06e16992ae1c41b0fc98ebcd07386c5381
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Een Microsoft Intune-abonnement instellen voor On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-premises Mobile Device Management is vereist voor een Microsoft Intune-abonnement om licenties te volgen. De Intune-service niet wordt gebruikt om de apparaten te beheren of management-gegevens op te slaan. Voor op\-premises Mobile Device Management, alle Apparaatbeheer wordt verwerkt door de Configuration Manager-infrastructuur.  

> [!NOTE]  
> Vanaf versie 1610, Configuration Manager ondersteunt het gebruik van zowel Microsoft Intune en on-premises Configuration Manager-infrastructuur voor het beheren van mobiele apparaten op hetzelfde moment.   

> [!TIP]  
>  Het is raadzaam dat u de Intune-abonnement voor op ingesteld\-premises Mobile Device Management voordat u de vereiste sitesysteemrollen installeren om te beperken van de tijd die nodig zijn voor de nieuw geïnstalleerde sitesysteemrollen functioneel te laten worden.  

##  <a name="sign-up-for-microsoft-intune"></a>Aanmelden voor Microsoft Intune  
 Intune is vereist voor het aanbrengen van\-premises Mobile Device Management functioneel. Gewoon [aanmelden](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) voor een proef- of betaald abonnement en Ga naar de volgende stap het abonnement wilt toevoegen aan Configuration Manager.  

##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Het Intune-abonnement toevoegen aan Configuration Manager  
 Om het abonnement aan Configuration Manager toevoegen, volgt u dezelfde basisstappen net als bij het toevoegen van het abonnement voor mobile device management met Intune. Lees de opmerkingen hieronder voor de specifieke verschillen en gebruik vervolgens de instructies in [uw Intune-abonnement configureren](../deploy-use/configure-intune-subscription.md).  

> [!NOTE]  
>  Houd rekening met het volgende bij het toevoegen van het Intune-abonnement:  
>   
>  -   De verzameling die is opgegeven in de Wizard Microsoft Intune-abonnement wordt niet gebruikt voor op\-premises Mobile Device Management gebruiker overdragen. Dit wordt alleen gebruikt voor het beheer van mobiele apparaten met Intune. U moet echter een verzameling opgeven om de wizard verder te laten gaan.  
> -   Instelling voor de sitecode opgegeven in de wizard wordt genegeerd voor op\-premises Mobile Device Management. De sitecode die wordt gebruikt is de sitecode die u opgeeft in het registratieprofiel waarmee u gebruikers toestemming verleent om apparaten te registreren.  
> -   Schakel Multi-Factor Authentication niet in. Wordt niet ondersteund in op\-premises Mobile Device Management.  

##  <a name="configure-the-intune-subscription-for-on-premises-mobile-device-management"></a>De Intune-abonnement voor On-premises Mobile Device Management configureren  

1.  In de Configuration Manager-console met de rechtermuisknop op de **Microsoft Intune-abonnement**, en klik op **eigenschappen**.  

2.  Kies een van de volgende opties in het vak op Premises Mobile Device Management:

  - Als u van plan bent om alleen apparaten on-premises worden beheerd, klikt u op het selectievakje in naast **alleen beheer van on-premises**, en klik op **OK**.  

      > [!NOTE]  
      >  Door u dit selectievakje inschakelt, moet u de Intune-abonnement om te behouden van alle informatie lokaal beheer en repliceert gegevens niet naar de cloud configureren.  

    - Als u van plan bent om apparaten die worden beheerd door Intune en Configuration Manager on-premises, laat u het vakje uitgeschakeld.

3.  Als u van plan bent om Windows 10 Mobile-apparaten te beheren, klik dan met de rechtermuisknop op het **Microsoft Intune-abonnement**, klik op **Platforms configureren**en klik vervolgens op  **Windows Phone**.  

4.  Schakel het selectievakje in naast **Windows Phone 8.1 en Windows 10 Mobile**en klik vervolgens op **OK**.  

5.  Als u van plan bent om Windows 10 Mobile-desktopcomputers te beheren, klik dan met de rechtermuisknop op het **Microsoft Intune-abonnement**, klik op **Platforms configureren**en klik vervolgens op **Windows-registratie inschakelen**.  

6.  Schakel het selectievakje in naast **Windows-registratie inschakelen**en klik vervolgens op **OK**.  
