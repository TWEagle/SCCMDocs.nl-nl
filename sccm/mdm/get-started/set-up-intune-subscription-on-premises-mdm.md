---
title: Instellen van Intune-abonnement | Microsoft-documenten
description: Instellen van een Intune-abonnement om bij te houden voor On-premises mobiele apparaten beheren in System Center Configuration Manager-licentieverlening.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: 8
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 5a81ec06e16992ae1c41b0fc98ebcd07386c5381
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Een abonnement op Microsoft Intune instellen voor On-premises mobiele apparaten beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-lokale beheer van mobiele apparaten is een Microsoft Intune-abonnement om bij te houden licentieverlening vereist. De Intune-service niet wordt gebruikt voor het beheren van de apparaten of voor het opslaan van beheergegevens. Voor op\-lokale beheer van mobiele apparaten, alle Apparaatbeheer kan worden opgelost door de Configuration Manager-infrastructuur.  

> [!NOTE]  
> Vanaf versie 1610 wordt Configuration Manager ondersteunt het gebruik van zowel Microsoft Intune en Configuration Manager-infrastructuur voor het beheren van mobiele apparaten op hetzelfde moment op locatie.   

> [!TIP]  
>  Het is raadzaam dat u instelt voor de Intune-abonnement voor\-premises beheer van mobiele apparaten, voordat u de vereiste sitesysteemrollen om de tijd die nodig is voor de nieuw geïnstalleerde sitesysteemrollen worden functionele installeert.  

##  <a name="sign-up-for-microsoft-intune"></a>Aanmelden voor Microsoft Intune  
 Intune is vereist voor het aanbrengen van\-beheer van mobiele apparaten functionele-premises. Gewoon [aanmelden](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) voor een proef- of betaald abonnement en Ga naar de volgende stap het abonnement toevoegen aan Configuration Manager.  

##  <a name="add-the-intune-subscription-to-configuration-manager"></a>De Intune-abonnement toevoegen aan Configuration Manager  
 Het abonnement voor Configuration Manager toevoegen, stappen u dezelfde basic zoals u zou doen tijdens het toevoegen van het abonnement voor beheer van mobiele apparaten met Intune. Lees de opmerkingen hieronder voor specifieke verschillen en gebruik vervolgens de instructies in [uw Intune-abonnement configureren](../deploy-use/configure-intune-subscription.md).  

> [!NOTE]  
>  Houd rekening met het volgende bij het toevoegen van de Intune-abonnement:  
>   
>  -   De verzameling die is opgegeven in de Wizard Microsoft Intune-abonnement wordt niet gebruikt voor op\-beheer van mobiele apparaten gebruiker de juiste delegatie-premises. Het wordt alleen gebruikt voor het beheer van mobiele apparaten met Intune. U moet echter een verzameling opgeven om de wizard verder te laten gaan.  
> -   De instelling voor de site opgegeven in de wizard wordt genegeerd voor op\-premises beheer van mobiele apparaten. De sitecode die wordt gebruikt is de sitecode die u opgeeft in het registratieprofiel waarmee u gebruikers toestemming verleent om apparaten te registreren.  
> -   Schakel Multi-Factor Authentication niet in. Het wordt niet ondersteund op\-premises beheer van mobiele apparaten.  

##  <a name="configure-the-intune-subscription-for-on-premises-mobile-device-management"></a>De Intune-abonnement voor beheer van lokale mobiele apparaten configureren  

1.  In de Configuration Manager-console met de rechtermuisknop op de **Microsoft Intune-abonnement**, en klikt u op **eigenschappen**.  

2.  Kies een van de volgende opties in het vak voor lokaal beheer van mobiele apparaten:

  - Als u van plan bent om alleen apparaten beheerde lokale, klikt u op het selectievakje in naast **alleen beheren van apparaten op de lokale**, en klikt u op **OK**.  

      > [!NOTE]  
      >  U configureert via dit selectievakje in de Intune-abonnement om alle gegevens lokaal beheer bewaren en gegevens niet gerepliceerd naar de cloud.  

    - Als u apparaten beheren met Intune en Configuration Manager op locatie, laat u het uitgeschakeld.

3.  Als u van plan bent om Windows 10 Mobile-apparaten te beheren, klik dan met de rechtermuisknop op het **Microsoft Intune-abonnement**, klik op **Platforms configureren**en klik vervolgens op  **Windows Phone**.  

4.  Schakel het selectievakje in naast **Windows Phone 8.1 en Windows 10 Mobile**en klik vervolgens op **OK**.  

5.  Als u van plan bent om Windows 10 Mobile-desktopcomputers te beheren, klik dan met de rechtermuisknop op het **Microsoft Intune-abonnement**, klik op **Platforms configureren**en klik vervolgens op **Windows-registratie inschakelen**.  

6.  Schakel het selectievakje in naast **Windows-registratie inschakelen**en klik vervolgens op **OK**.  

