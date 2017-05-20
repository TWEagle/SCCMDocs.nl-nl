---
title: Apparaten met IMEI-nummer of iOS-serienummers predeclare | Microsoft-documenten
description: Apparaten in Bedrijfseigendom met hun IMEI-nummer of iOS-serienummer predeclare.
ms.custom: na
ms.date: 03/24/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: 3
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6833951db27b227a3ca22925e9d9f4c3fc443fc
ms.openlocfilehash: e8606b8a9268a0a0668b75070cf35894f4794123
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers predeclare

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt apparaten in Bedrijfseigendom identificeren door hun internationale station mobile equipment identity (IMEI) getallen of iOS-serienummers importeren. U kunt een apparaat IMEI getallen met door komma's gescheiden waarden (.csv)-bestand uploaden of u kunt de apparaatgegevens handmatig invoeren.  Geïmporteerde gegevens wordt ingesteld **eigendom** van de apparaten die worden ingeschreven als **bedrijf** in een lijst met apparaten. Een licentie voor Intune is nog steeds vereist is voor elke gebruiker die toegang de service.  

Tijdens het uploaden van serienummers voor bedrijf iOS-apparaten moeten deze worden gekoppeld aan een profiel voor bedrijfsinschrijving. Apparaten moeten vervolgens met behulp van een van beide Apples apparaatinschrijvingsprogramma (DEP) of Apple Configurator hebben ze worden weergegeven als eigendom van het bedrijf zijn ingeschreven.

## <a name="how-to-predeclare-corporate-owned-devices"></a>Hoe predeclare apparaten in Bedrijfseigendom

1.    Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **Predeclared apparaten**.

2.  Klik op **Predeclared apparaten maken**. De wizard Predeclared apparaten maken wordt geopend.

3.    Kiezen hoe u wilt toevoegen, apparaatgegevens:

     -    **Een CSV-bestand met IMEI-nummer of de serienummers en details uploaden**

        Deze optie, klikt u op **Bladeren** om op te geven van het CSV-bestand met de gegevens voor apparaten in Bedrijfseigendom predeclare. Het CSV-bestand moet de juiste notatie. Zie voor meer informatie [indeling voor het CSV-bestanden uploaden](#format-for-uploading-csv-files).

     -    **IMEI-nummer of de serienummers en gegevens handmatig toevoegen**

        Typ de IMEI-nummer of iOS-serienummer en details van de apparaten die u handmatig hebt ingevoerd. Corrigeer eventuele fout of waarschuwingen voordat u doorgaat.

    Klik op **Volgende**.

4. Als u een CSV-bestand hebt geüpload, bekijkt u de resultaten van het bestand importeren. Als een telefoonnummer is eerder is geïmporteerd, Configuration Manager weergeeft die apparaten en de vervanging **Details**. Selecteer de apparaten waarvan de gegevens u wilt overschrijven. Apparaatdetails kunnen alleen worden gewijzigd door de apparaat-id of het serienummer opnieuw te importeren.

  Als u kiest voor het handmatig invoeren, vult u het formulier voor de apparaten die u wilt predeclare.

  Klik op **Volgende** om verder te gaan.

4. Als uw lijst met iOS-serienummers bevat, selecteert u de **Inschrijvingsprofiel toe te wijzen** uit de lijst met beschikbare profielen en klik vervolgens op **volgende**.

5. Klik op **volgende** Lees de informatie en klik vervolgens op **volgende** opnieuw de gegevens te uploaden.

6. Klik op **sluiten** te voltooien.

## <a name="format-for-uploading-csv-files"></a>Indeling voor het uploaden van CSV-bestanden

Het CSV-bestand dat u gebruiken om apparaten door IMEI-nummer of een serienummer te identificeren, moet de volgende indeling, met uitzondering van de eerste rij die aanwezig voor alleen richtlijnen hebben. Elke rij moet bevatten een id-nummer, ofwel een serienummer IMEI-nummer of iOS. U kunt beide opnemen. IMEI-nummer cijfers kan worden gebruikt voor Android, iOS en Windows-apparaten. iOS-serienummers worden ook ondersteund.  Deze tabel bevat de voorbeeldgegevens:

| IMEI-NUMMER #  | iOS seriële #  | BESTURINGSSYSTEEM | Details |
|------------ |---------------|-----|-----|
| 123456789012345    |   | WINDOWS | Eigendom van het bedrijf van de Windows-apparaat|
|   | A1B2C3D4E5C6 | IOS |     Eigendom van het bedrijf iOS-apparaat|
| 223456789012345 | E6D5C4B3A210 |   IOS |     Een andere iOS-apparaat|
| 323456789012345 |        |   IOS |     Een derde iOS-apparaat|
| 123456789012346 |         |   ANDROID |     Eigendom van het bedrijf Android-apparaat|

Een veldnamenrij is niet inbegrepen in uw CSV-bestand. Het volgende voorbeeld ziet u de dezelfde voorbeeldgegevens in CSV-indeling:

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
|IMEI-nummer zonder spaties | iOS-serienummer | IOS-, WINDOWS- of ANDROID | Optionele Apparaatdetails (maximaal 1024 tekens) |

