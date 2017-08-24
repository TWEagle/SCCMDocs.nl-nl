---
title: Mogelijkheden in Technical Preview 1704 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1704.
ms.custom: na
ms.date: 4/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d7caee47ca74064630e09c1bdb94187af256d4b4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1704 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1704 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>Android-apps met app-configuratiebeleid configureren
Kunt u app-configuratiebeleid in System Center Configuration Manager (Configuration Manager) voor het distribueren van de instellingen die mogelijk vereist zijn wanneer een gebruiker een app uitvoert op Android voor Work-apparaten. Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work en gelden voor goedgekeurde apps uit de Play voor werk store.

### <a name="try-it-out"></a>Try it out in                 

Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **Configuratiebeleidsregels** en kies **App-configuratiebeleid maken**. Op de **algemene** pagina van de wizard kunt u nu **selecteert u een beleidstype configuratie**. Geef het platform waarop de app-configuratiebeleid: **Configuratiebeleid voor Android voor zakelijke apps**. U kunt vervolgens ofwel **naam- en waardeparen opgeven** of **Blader naar een lijst met JSON-bestand van de eigenschap**. De nieuwe app-configuratiebeleid wordt weergegeven in de **softwarebibliotheek** werkruimte, in de **Configuratiebeleidsregels** knooppunt. Als u wilt een app-configuratiebeleid koppelen aan de implementatie van een Android voor werk app, implementeert u de toepassing normaal met behulp van de procedure in de [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications) onderwerp.

## <a name="hardware-inventory-collects-secure-boot-information"></a>Hardware-inventaris verzamelt gegevens van beveiligd opstarten
Hardware-inventaris verzamelt nu informatie over of beveiligd opstarten is ingeschakeld op clients. Deze informatie wordt opgeslagen in de **SMS_Firmware** klasse (geïntroduceerd in versie 1702) en ingeschakeld in hardware-inventarisatie standaard. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Takenreeksen onderliggende toevoegen aan een takenreeks
In deze versie kunt u een nieuwe takenreeksstap met een andere takenreeks die u een bovenliggende/onderliggende relatie tussen de takenreeksen maakt toevoegen. Hiermee kunt u meer modulaire takenreeksen maken die u opnieuw kunt gebruiken.  

Overweeg het volgende wanneer u een takenreeks onderliggende aan een takenreeks toevoegt:

- De bovenliggende en onderliggende takenreeksen effectief gecombineerd tot een enkele beleidsregel die de client wordt uitgevoerd.
- Toevoegen van een onderliggende takenreeks die een bovenliggende schijf van een andere takenreeks wordt niet ondersteund.
- De omgeving is algemeen. Bijvoorbeeld, als een variabele is ingesteld door de takenreeks voor de bovenliggende en vervolgens worden gewijzigd door de onderliggende takenreeks wordt uitgevoerd, de variabele blijft gewijzigd zwevend doorsturen. Op dezelfde manier als de onderliggende takenreeks maakt u een nieuwe variabele, is de variabele beschikbaar voor de overige stappen in de takenreeks bovenliggende.
- Statusberichten worden voor een enkele takenreeksbewerking per normaal verzonden.
- De takenreeksen vermeldingen schrijven naar het bestand smsts.log met nieuwe logboekbestanden vermeldingen die duidelijk wanneer een onderliggende takenreeks wordt gestart.
- In de Technical Preview voor Configuration Manager versie 1704, als de onderliggende takenreeksen verwijst naar een pakket en u de bovenliggende takenreeks vanuit Software Center uitvoert, wordt de client niet gevonden inhoud van het pakket wanneer de onderliggende takenreeks wordt uitgevoerd. In dit scenario moet u de takenreeks vanaf media uitvoeren (starten media, PXE, enz.).  

    Als de onderliggende takenreeks maakt gebruik van stappen zoals **opdrachtregel uitvoeren** (zonder een pakket-verwijzing) **indeling**, **BitLocker**, enz., en vervolgens de takenreeks wordt uitgevoerd vanuit Software Center.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Een takenreeks onderliggende toevoegen aan een takenreeks
1. Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en klik op **Takenreeks uitvoeren**.
2. Klik op **Bladeren** naar de onderliggende takenreeks selecteren.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>Laden van installatiekopieën voor opstarten met huidige Windows PE-versie
Bij het uitvoeren van **distributiepunten bijwerken** op een geselecteerde opstartinstallatiekopie, kunt u nu kiezen om opnieuw te laden van de nieuwste versie van Windows PE (van de installatiemap van Windows ADK) in de opstartinstallatiekopie. De **algemene** pagina van de wizard bevat informatie over de Windows ADK-versie die is geïnstalleerd op de siteserver, de Windows ADK-versie waarin Windows PE wordt gebruikt in de opstartinstallatiekopie en de versie van Configuration Manager-client. U kunt deze informatie gebruiken om te beslissen of u wilt de opstartinstallatiekopie opnieuw laden. Ook een nieuwe kolom (**clientversie**) is toegevoegd wanneer u opstartinstallatiekopieën in de **opstartinstallatiekopieën** knooppunt zodat u weet welke versie van Configuration Manager-client elke opstartinstallatiekopie wordt gebruikt.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>Opnieuw laden van een installatiekopie met de huidige versie van Windows PE

1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **opstartinstallatiekopieën**.
2. Een opstartinstallatiekopie selecteren en op **distributiepunten bijwerken**.
3. Op de **algemene** pagina van de wizard de optie **opstartinstallatiekopie opnieuw laden met behulp van de huidige versie van Windows PE van de geïnstalleerde Windows-ADK**.

## <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
We hebben de volgende verbeteringen aangebracht in de implementatie van besturingssystemen, die het resultaat van uw stem feedback van gebruikers zijn aangebracht.

- [Nieuwe **besturingssysteemversie** kolom voor installatiekopieën van besturingssystemen](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): We hebben een nieuwe kolom die met de naam toegevoegd **besturingssysteemversie** om weer te geven van de versie van het besturingssysteem voor de installatiekopie wanneer u informatie bekijken in de **installatiekopieën van besturingssystemen** en **besturingssysteem Upgrade-pakketten** knooppunten. Alleen de versie van de eerste index in de. WIM wordt weergegeven. Ga naar de **Details** tabblad voor de installatiekopie besturingssysteemversies voor andere indexen bekijken.

- [Efficiëntere logboekregistratie in Smsts.log](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): Vanaf deze versie, zijn wij niet langer vermeldingen schrijven naar het bestand smsts.log voor CCM_CIVersionInfo.PolicyID informatie. Voor deze versie kan er een groot aantal vermeldingen met deze informatie, waardoor het moeilijk te vinden van meest relevante gegevens in het logboekbestand.
