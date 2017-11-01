---
title: Het beheren van naleving op apparaten worden beheerd door Intune
titleSuffix: Configuration Manager
description: Meer informatie over System Center Configuration Manager-instellingen voor naleving door het uitvoeren van enkele algemene scenario's.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e83007f-e81c-4b7e-b47e-b01d7b19cfbc
caps.latest.revision: "5"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 97f0ed47447dc5603a65563b0e87ec90bcc1fe42
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="managing-compliance-on-devices-managed-with-intune"></a>Het beheren van naleving op apparaten worden beheerd door Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze scenario's bieden u een inleiding tot het gebruik van System Center Configuration Manager-instellingen voor naleving door het uitvoeren van enkele algemene scenario's die u kunt tegenkomen.  

 Als u al bekend met instellingen voor naleving bent, gedetailleerde documentatie over functies die u gebruikt kan worden gevonden in de [configuratie-items voor apparaten die worden beheerd door Intune](#configuration-items-for-devices-managed-with-intune) sectie.  

 [Aan de slag met instellingen voor naleving](../../compliance/get-started/get-started-with-compliance-settings.md) biedt u de basisbeginselen van nalevingsinstellingen en [plannen en configureren van instellingen voor naleving](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) helpt u alle benodigde voorwaarden te implementeren.  

## <a name="general-information-for-each-scenario"></a>Algemene informatie voor elk scenario  
 In elk scenario maakt u een configuratie-item waarmee een specifieke taak wordt uitgevoerd. Open de wizard Configuratie-item maken en voer de volgende stappen uit:  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **configuratie-Items**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  

4.  Geef op het tabblad **Algemeen** van de wizard Configuratie-item maken een naam en beschrijving op voor het configuratie-item, zoals hieronder wordt weergegeven. Kies vervolgens het juiste configuratie-itemtype voor elk scenario in dit onderwerp.  

     ![Pagina Algemeen van de configuratiewizard-item bevat.](media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-81-and-windows-10-devices-managed-with-intune"></a>Scenario's voor Windows 8.1 en Windows 10-apparaten worden beheerd door Intune  

### <a name="scenario-restrict-access-to-the-app-store-on-all-windows-pcs"></a>Scenario: Beperk de toegang tot de appstore op alle Windows-pc 's  
 In dit scenario bent u de IT-beheerder voor een bedrijf dat werkt met uiterst gevoelige informatie. U legt daarom beperkingen op voor de apps die gebruikers kunnen installeren. U wilt voorkomen dat gebruikers van alle Windows 10-computers apps downloaden van de Windows Store en onderneemt daarom de volgende acties.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **Windows 8.1 en Windows 10** en klik vervolgens op **Volgende**.  

2.  Op de **ondersteunde Platforms** pagina, selecteert u alle Windows 10-platforms.  

3.  Selecteer op de pagina **Apparaatinstellingen** de optie **Store**en klik vervolgens op **Volgende**.  

4.  Selecteer op de pagina **Store** de optie **Niet toegestaan** als waarde voor **App Store**.  

5.  Selecteer **Niet-compatibele instellingen herstellen** zodat de wijziging wordt toegepast op alle pc’s.  

6.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  

## <a name="scenarios-for-windows-phone-devices-managed-with-intune"></a>Scenario's voor Windows Phone-apparaten die worden beheerd met Intune  

### <a name="scenario-disable-the-use-of-screen-capture-on-a-windows-phone"></a>Scenario: Het gebruik van schermafbeeldingen op een Windows Phone uitschakelen  
 In dit scenario gebruikt u Windows Phone 8.1-apparaten in uw bedrijf. Op deze apparaten wordt een verkoop-app uitgevoerd die gevoelige informatie bevat. Ter bescherming van uw bedrijf wilt u het gebruik van schermafbeeldingen op het apparaat uitschakelen. Deze zouden namelijk kunnen worden gebruikt om gevoelige informatie van uw bedrijf naar buiten te smokkelen.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **Windows Phone** en klik vervolgens op **Volgende**.  

2.  Op de **ondersteunde Platforms** pagina **alle Windows Phone 8.1** platforms.  

3.  Selecteer op de pagina **Apparaatinstellingen** de optie **Apparaat**en klik vervolgens op **Volgende**.  

4.  Selecteer op de pagina **Apparaat** de optie **Uitgeschakeld** als de waarde voor **Schermafbeelding**.  

5.  Selecteer **Niet-compatibele instellingen herstellen** zodat de wijziging wordt toegepast op alle Windows Phone 8.1-apparaten.  

6.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen met System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  

## <a name="scenarios-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Scenario's voor iOS en Mac OS X-apparaten worden beheerd door Intune  

### <a name="scenario-disable-the-camera-on-ios-devices"></a>Scenario: De camera op iOS-apparaten uitschakelen  
 In dit scenario produceert uw bedrijf blauwdrukken voor nieuwe productontwerpen. Deze bevatten vertrouwelijke informatie die niet naar buiten mag worden gebracht. Als uw bedrijf alle werknemers voorziet van iPhone's en iPads, wilt u het gebruik van de camera op deze apparaten uitschakelen om te voorkomen dat ze worden gebruikt om de blauwdrukken te fotograferen.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **iOS en Mac OS X** en klik vervolgens op **Volgende**.  

2.  Op de **ondersteunde Platforms** pagina, selecteert u alle iPhone- en alle iPad-apparaatplatformen.  

3.  Selecteer op de pagina **Apparaatinstellingen** de optie **Beveiliging**en klik vervolgens op **Volgende**.  

4.  Selecteer op de pagina **Beveiliging** de optie **Niet toegestaan** als waarde voor **Camera**.  

5.  Selecteer **Niet-compatibele instellingen herstellen** zodat de wijziging wordt toegepast op alle iOS-apparaten.  

6.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen met System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  

## <a name="scenarios-for-android-and-samsung-knox-standard-devices-managed-with-intune"></a>Scenario's voor Android en Samsung KNOX Standard-apparaten worden beheerd door Intune  

### <a name="scenario-require-a-password-on-all-android-5-devices"></a>Scenario: Een wachtwoord vereisen bij alle Android 5-apparaten  
 In dit scenario maakt u uitsluitend voor Android 5-apparaten een configuratie-item waarmee gebruikers verplicht worden gesteld om een wachtwoord van ten minste zes tekens op hun apparaten te configureren. Bovendien worden alle gegevens op het apparaat gewist, als een gebruiker vijf maal een onjuist wachtwoord heeft ingevoerd.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **Android en Samsung KNOX** en klik vervolgens op **Volgende**.  

2.  Op de **ondersteunde Platforms** pagina, selecteert u alleen **Android 5** (om te zorgen dat de instellingen alleen toegepast op dat platform).  

3.  Selecteer op de pagina **Apparaatinstellingen** de optie **Wachtwoord**en klik vervolgens op **Volgende**.  

4.  Configureer op de pagina **Wachtwoord** de volgende instellingen:  

    -   **Wachtwoordinstellingen verplicht stellen op apparaten** > **Verplicht**  

    -   **Minimale wachtwoordlengte (tekens)** > **6**  

    -   **Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist** > **5**  

5.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  

## <a name="configuration-items-for-devices-managed-with-intune"></a>Configuratie-items voor apparaten die worden beheerd met Intune

System Center Configuration Manager configuratie-items die zijn beschikbaar voor apparaten die niet worden beheerd door de Configuration Manager-client, bijvoorbeeld apparaten die zijn geregistreerd bij Microsoft Intune.  

 -   [Het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd door Intune](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)  

 -   [Het maken van configuratie-items voor Windows Phone-apparaten die worden beheerd met Intune](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)  

 -   [Het maken van configuratie-items voor iOS en Mac OS X-apparaten worden beheerd door Intune](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)  

 -   [Het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten worden beheerd door Intune](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)  
