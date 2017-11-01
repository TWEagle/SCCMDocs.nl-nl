---
title: Apparaten met IMEI-nummer of iOS-serienummers labelen
titleSuffix: Configuration Manager
description: Apparaten in Bedrijfseigendom met hun IMEI-nummer of iOS-serienummer labelen.
ms.custom: na
ms.date: 09/01/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: "3"
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: a58c765833fe1ef65c2497fd1e2d079caa3f2ff3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers labelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt apparaten in Bedrijfseigendom identificeren met hun nummers van international station mobile equipment identity (IMEI-nummer) of een iOS-serienummers importeren. U kunt een door komma's gescheiden waarden (.csv)-bestand met IMEI-nummers van apparaten uploaden of u kunt de apparaatgegevens handmatig invoeren.  Geïmporteerde gegevens wordt ingesteld **eigendom** van de apparaten die worden ingeschreven als **zakelijk** in een lijst met apparaten. Een Intune-licentie is nog steeds vereist zijn voor elke gebruiker die toegang heeft tot de service.  

Tijdens het uploaden van serienummers van bedrijfseigen iOS-apparaten, moeten ze worden gekoppeld aan een inschrijvingsprofiel voor bedrijfsapparaten. Apparaten moeten vervolgens beide Apples apparaatinschrijvingsprogramma (DEP) of Apple Configurator gebruiken om u te laten verschijnen als eigendom van het bedrijf zijn ingeschreven.

>[!NOTE]
>Android-apparaten, met uitzondering van Samsung Knox Standard-apparaten, moeten een telefoonnummer aan hen toegewezen om te labelen en registreren als een apparaat in Bedrijfseigendom met IMEI-nummer hebben.

## <a name="how-to-predeclare-corporate-owned-devices"></a>Het labelen van apparaten in Bedrijfseigendom

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **Predeclared apparaten**.

2.  Klik op **Predeclared apparaten maken**. De wizard Predeclared apparaten maken wordt geopend.

3.  Kies hoe u gegevens van een apparaat wilt:

     -  **Een CSV-bestand met IMEI- of serienummers en details uploaden**

        Voor deze optie, klikt u op **Bladeren** om op te geven van het CSV-bestand met de gegevens voor het labelen van apparaten in Bedrijfseigendom. Het CSV-bestand moet de juiste notatie. Zie voor meer informatie [indeling voor het uploaden van CSV-bestanden](#format-for-uploading-csv-files).

     -  **IMEI- of serienummers en gegevens handmatig toevoegen**

        Als u wilt gegevens handmatig invoeren, typt u de IMEI-nummer of iOS-serienummer en de details voor de apparaten. Corrigeer eventuele fout of waarschuwingen voordat u doorgaat.

    Klik op **Volgende**.

4. Als u een CSV-bestand hebt geüpload, bekijk de resultaten van het bestand importeren. Als een apparaat-getal is eerder geïmporteerd, Configuration Manager weergeeft die apparaten en de vervanging **Details**. Selecteer de apparaten waarvan details die u wilt overschrijven. Apparaatdetails kunnen alleen worden gewijzigd door de apparaat-id of het serienummer opnieuw te importeren.

  Als u zelf nummer invoert kiest, vult u het formulier voor de apparaten die u wilt labelen.

  Klik op **Volgende** om verder te gaan.

4. Als uw lijst met iOS-serienummers bevat, selecteert de **Inschrijvingsprofiel toe te wijzen** uit de lijst met beschikbare profielen en klik vervolgens op **volgende**.

5. Klik op **volgende** Lees de informatie en klik vervolgens op **volgende** opnieuw de gegevens te uploaden.

6. Klik op **sluiten** te voltooien.

## <a name="format-for-uploading-csv-files"></a>Indeling voor het uploaden van CSV-bestanden

Het CSV-bestand dat u gebruikt om apparaten te identificeren op IMEI-nummer of iOS-serienummer moet de volgende indeling, met uitzondering van de bovenste rij die wordt ondersteund voor richtlijnen alleen hebben. Elke rij moet een id-nummer, een IMEI-nummer of iOS-serienummer bevatten. U kunt beide opnemen voor iOS-apparaten. IMEI-nummers kan worden gebruikt voor Android, iOS en Windows-apparaten. Deze tabel bevat de voorbeeldgegevens:

| IMEI-NUMMER #  | iOS seriële #  | BESTURINGSSYSTEEM | Details |
|------------ |---------------|-----|-----|
| 123456789012345    |   | WINDOWS | Windows-apparaat eigendom van het bedrijf|
|   | A1B2C3D4E5C6 | IOS |  Bedrijfseigen iOS-apparaat|
| 223456789012345 | E6D5C4B3A210 |   IOS |  Een ander iOS-apparaat|
| 323456789012345 |        |   IOS |    Een derde iOS-apparaat|
| 123456789012346 |         |   ANDROID |   Android-apparaat eigendom van het bedrijf|

Een veldnamenrij niet opnemen in uw CSV-bestand. Het volgende voorbeeld ziet de dezelfde voorbeeldgegevens in CSV-indeling:

```
123456789012345,,WINDOWS,Company-owned Windows device
,A1B2C3D4E5C6,IOS,Company-owned iOS device
223456789012345,E6D5C4B3A210,IOS,Another iOS device
323456789012345,,IOS,A third iOS device
123456789012346,,ANDROID,Company-owned Android device
```

De kolommen in het CSV-bestand accepteren de volgende waarden:

| Kolom 1 | Kolom 2 | Kolom 3 | Kolom 4 |
|---|---|---|---|
|IMEI-nummer zonder spaties | iOS-serienummer | IOS-, WINDOWS- of ANDROID | Details van de optionele apparaat (maximaal 1024 tekens) |
