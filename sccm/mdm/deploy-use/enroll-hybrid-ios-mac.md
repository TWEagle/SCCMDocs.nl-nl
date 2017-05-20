---
title: IOS en Mac hybride Apparaatbeheer met System Center Configuration Manager en Microsoft Intune instellen | Microsoft-documenten
description: Beheer van iOS-apparaten met System Center Configuration Manager en Microsoft Intune instellen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
caps.latest.revision: 10
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 02af275ede0ab8578adb0615458b285819d65c9c
ms.openlocfilehash: 848721b564316234ad900fcbf968098002a4bb4e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Beheer van hybride iOS-apparaten met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met Configuration Manager en Intune, kunt u BYOD iOS ('bring your own device') en de inschrijving voor Mac OS X-apparaten toegang geven tot bedrijfse-mail en bronnen voor iPhone, iPad en Mac-gebruikers. Als gebruikers de Intune-bedrijfsportal-app installeren, kunnen hun apparaten doelgericht van beleid worden voorzien. Voordat u iOS- en Mac-apparaten kunt beheren, moet u een APNs-certificaat (Apple Push Notification-service) van Apple importeren. Met dit certificaat kan Intune iOS- en Mac-apparaten beheren en wordt er een erkende en versleutelde IP-verbinding tot stand gebracht met de services van de Mobile Device Management-autoriteit.  

 U kunt ook zakelijke iOS-apparaten inschrijven.  Zie [apparaten van het bedrijf inschrijven](enroll-company-owned-devices.md).  

## <a name="enable-ios-device-enrollment"></a>Inschrijving van iOS-apparaten inschakelen  
 U moet deze stappen volgen om de registratie van iOS-apparaten te ondersteunen:  

#### <a name="set-up-ios-device-enrollment-in-configuration-manager"></a>Inschrijving van iOS-apparaten in Configuration Manager instellen  

1.  **Vereisten** - voordat u met inschrijving voor elk platform en instellen kunt Voltooi de vereisten en de procedures in [Setup hybride MDM](setup-hybrid-mdm.md).    

2.  **Download een certificaatondertekeningaanvraag** : een CSR-bestand (certificaatondertekeningsaanvraag) is vereist om een APNs-certificaat van Apple aan te kunnen vragen.  

    1.  Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices**> **Microsoft Intune-abonnementen**.  

    2.  Klik op het tabblad **Start** op **APNs-certificaataanvraag maken**. Het dialoogvenster **Aanvraag voor Apple Push Notification Service-certificaatondertekening aanvragen** wordt geopend.  

    3.  **Blader** naar het pad om het nieuwe aanvraagbestand tot certificaatondertekening (.csr) op te slaan. Sla het bestand met de aanvraag voor certificaatondertekening (.csr) lokaal op.  

    4.  Klik op **Downloaden**. Het nieuwe Microsoft Intune CSR-bestand wordt gedownload en door Configuration Manager opgeslagen. Het CSR-bestand wordt gebruikt voor het aanvragen van een vertrouwensrelatiecertificaat uit de Apple Push Certificates Portal.  

3.  **Een APNs-certificaat bij Apple aanvragen** : het APNs-certificaat (Apple Push Notification-service) wordt gebruikt om een vertrouwensrelatie tussen de beheerservice, Intune en ingeschreven mobiele iOS-apparaten te maken.  

    1.  Ga in een browser naar de [Apple Push Certificates-portal](http://go.microsoft.com/fwlink/?LinkId=269844) en meld u aan met de Apple-id van uw bedrijf. Deze Apple-id moet in de toekomst worden gebruikt om uw APNs-certificaat te vernieuwen.  

    2.  Voltooi de wizard met behulp van het CSR-bestand. Download het APNs-certificaat en sla het .pem-bestand lokaal op. Dit APNs-certificaatbestand (.pem) wordt gebruikt voor het opzetten van een vertrouwensrelatie tussen de Apple Push Notification-server en de Intune mobile device management-instantie.  

4.  **Schakel inschrijving in en upload het APNs-certificaat** : u moet het APNs-certificaat uploaden om iOS-inschrijving in te schakelen.  

    1.  Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices** > **Microsoft Intune-abonnement**.  

    2.  Op het tabblad **Start** in de groep **Abonnement** klikt u op **Platforms configureren** > **iOS**.  

        > [!NOTE]  
        >  Upload het APNs-certificaat (Apple Push Notification Service) pas nadat u iOS-inschrijving in de Configuration Manager-console hebt ingeschakeld.  

    3.  Selecteer in het dialoogvenster **Eigenschappen van Microsoft Intune-abonnement** het tabblad **iOS** en klik om het selectievakje **iOS-inschrijving inschakelen** in te schakelen.  

    4.  Klik op **Bladeren**en ga naar het APNs-certificaatbestand (.cer) dat u bij Apple hebt gedownload. Configuration Manager geeft de APNs-certificaatinformatie weer. Klik op **OK** om het APNs-certificaat op te slaan in Intune.  

 Zodra u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze hun apparaten moeten inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)

