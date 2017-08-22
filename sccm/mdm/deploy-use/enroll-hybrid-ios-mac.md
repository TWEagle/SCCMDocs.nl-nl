---
title: IOS en Mac hybride Apparaatbeheer met System Center Configuration Manager en Microsoft Intune instellen | Microsoft Docs
description: Beheer van iOS-apparaten met System Center Configuration Manager en Microsoft Intune instellen.
ms.custom: na
ms.date: 08/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
caps.latest.revision: "10"
caps.handback.revision: "0"
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: d84d6f3dba65f1d8114ef2eef9f19a2bb5389027
ms.sourcegitcommit: 9a6f8e028fb5eb2e752da70f42a5b548339bd8f4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/14/2017
---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Beheer van hybride iOS-apparaten met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met Configuration Manager en Intune, kunt u iOS- en Mac OS apparaatinschrijving toegang geven tot zakelijke e-mail en bronnen voor iPhone, iPad- en Mac-gebruikers inschakelen. Als gebruikers de Intune-bedrijfsportal-app installeren, kunnen hun apparaten doelgericht van beleid worden voorzien. Voordat u iOS- en Mac-apparaten kunt beheren, moet u een APNs-certificaat (Apple Push Notification-service) van Apple importeren. Dit certificaat kan Intune iOS- en Mac-apparaten beheren door een verbinding met Apples device management-service maken.  

 U kunt ook zakelijke iOS-apparaten inschrijven.  Zie [apparaten in Bedrijfseigendom inschrijven](enroll-company-owned-devices.md).  

**Vereisten**<br>
Voordat u inschrijven voor elk platform instellen kunt, voldoen aan de vereisten en procedures in [Setup hybride MDM](setup-hybrid-mdm.md).

U moet deze stappen volgen om de registratie van iOS-apparaten te ondersteunen:  

## <a name="download-a-certificate-signing-request"></a>Een aanvraag voor Certificaatondertekening downloaden
Een certificaat CSR-bestand is vereist een APNs-certificaat aanvragen bij Apple.  

1.  Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices**> **Microsoft Intune-abonnementen**.  

2.  Klik op het tabblad **Start** op **APNs-certificaataanvraag maken**. Het dialoogvenster **Aanvraag voor Apple Push Notification Service-certificaatondertekening aanvragen** wordt geopend.  

3.  **Blader** het pad naar het nieuwe certificaat CSR-bestand opslaan. Sla het aanvraagbestand lokaal op voor Certificaatondertekening.  

4.  Klik op **Downloaden**. De nieuwe Microsoft Intune Certificaatondertekening aanvragen bestandsdownloads en worden opgeslagen door Configuration Manager. Het certificaat CSR-bestand wordt gebruikt voor het aanvragen van een vertrouwensrelatiecertificaat uit de Apple Push Certificates-Portal.  

## <a name="request-an-mdm-push-certificate-from-apple"></a>Een MDM-Push-certificaat van Apple aanvragen
De MDM-Push-certificaat wordt gebruikt om een vertrouwensrelatie tussen de beheerservice, Intune en ingeschreven iOS-apparaten te maken.  

1.  Ga in een browser naar de [Apple Push Certificates-portal](http://go.microsoft.com/fwlink/?LinkId=269844) en meld u aan met de Apple-id van uw bedrijf. Deze Apple-id moet in de toekomst worden gebruikt om uw APNs-certificaat te vernieuwen.  

2.  Voltooi de wizard met behulp van het CSR-bestand. Download het MDM-Push-certificaat en sla het pem-bestand lokaal. Dit certificaatbestand (.pem) wordt gebruikt om een vertrouwensrelatie tussen de Apple Push Notification-server en de instantie voor mobile device management van Intune te maken.  

> [!NOTE]  
>  Upload het certificaat van Apple Push Notification service (APNs) niet bij Intune, totdat u iOS-inschrijving in de Configuration Manager-console inschakelen.  

## <a name="enable-enrollment-and-upload-the-mdm-push-certificate"></a>Schakel inschrijving in en upload het MDM-Push-certificaat
Upload het APNs-certificaat zodat iOS-inschrijving.  

1.  Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices** > **Microsoft Intune-abonnement**.  

2.  Op het tabblad **Start** in de groep **Abonnement** klikt u op **Platforms configureren** > **iOS**.  

3.  Selecteer in het dialoogvenster **Eigenschappen van Microsoft Intune-abonnement** het tabblad **iOS** en klik om het selectievakje **iOS-inschrijving inschakelen** in te schakelen.  
4.  Klik op **Bladeren**en ga naar het APNs-certificaatbestand (.cer) dat u bij Apple hebt gedownload. Configuration Manager geeft de APNs-certificaatinformatie weer. Klik op **OK** om het APNs-certificaat op te slaan in Intune.  

Nadat u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze kunnen hun apparaten inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/end-user-educate). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

## <a name="configure-enrollment-restrictions"></a>Beperkingen voor inschrijving configureren

Apparaten die door het blokkeren van persoonlijk eigendom zijn van apparaten kunnen inschrijven, kunt u beperken. Dit voorkomt dat gebruikers hun apparaten via de bedrijfsportal registreren. Persoonlijke apparaten te blokkeren, worden alleen de volgende apparaten kunnen inschrijven:
- [Predeclared apparaten](predeclare-devices-with-hardware-id.md)
- [Apple Configurator beheerde apparaten](ios-hybrid-enrollment-using-apple-configurator.md)
- [Device Enrollment Program (DEP) beheerde apparaten](ios-device-enrollment-program-for-hybrid.md)
- Apparaten die zijn geregistreerd met een [apparaatinschrijvingsbeheerder-account](enroll-devices-with-device-enrollment-manager.md)

### <a name="to-enable-enrollment-restrictions"></a>Inschakelen van beperkingen voor inschrijving
1.  Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices** > **Microsoft Intune-abonnement**.
2.  Op het tabblad **Start** in de groep **Abonnement** klikt u op **Platforms configureren** > **iOS**.
3.  Kies **blok persoonlijk eigendom zijn van apparaten** limiet inschrijving naar apparaten in Bedrijfseigendom.

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)
