---
title: Mogelijkheden in Technical Preview 1704 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1704.
ms.custom: na
ms.date: 4/21/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: d7caee47ca74064630e09c1bdb94187af256d4b4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1704 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1704 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>Android-apps configureren met app-configuratiebeleid
U kunt app configuratiebeleid in System Center Configuration Manager (Configuration Manager) distribueren instellingen die vereist zijn kunnen wanneer een gebruiker een app wordt uitgevoerd op Android voor werk apparaten. Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work en goedgekeurde apps van de Play voor werk store toepassen.

### <a name="try-it-out"></a>Probeer het nu                 

Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **App configuratiebeleid** en kies **App configuratiebeleid maken**. Op de **algemeen** pagina van de wizard kunt u nu **selecteert u een beleid configuratietype**. Geef de doelgroep van het app-configuratiebeleid platform: **Configuratiebeleid voor Android voor zakelijke apps**. U kunt vervolgens een **Geef naam- en waardeparen** of **bladert u naar een bestand eigenschappenlijst JSON**. Het nieuwe beleid van de app-configuratie wordt weergegeven in de **softwarebibliotheek** werkruimte in de **App configuratiebeleid** knooppunt. Implementeer de toepassing als u wilt een app-configuratiebeleid koppelen aan de implementatie van een Android voor werk app, zoals u dat gewend bent met de procedure in de [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications) onderwerp.

## <a name="hardware-inventory-collects-secure-boot-information"></a>Hardware-inventaris verzamelt informatie beveiligd opstarten
Hardware-inventaris verzamelt nu informatie over of beveiligd opstarten is ingeschakeld op clients. Deze informatie wordt opgeslagen in de **SMS_Firmware** klasse (geïntroduceerd in versie 1702) en ingeschakeld in hardware-inventaris standaard. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Onderliggende takenreeksen toevoegen aan een takenreeks
In deze versie kunt u een nieuwe takenreeksstap met een andere takenreeks die u een bovenliggende/onderliggende relatie tussen de takenreeksen maakt toevoegen. Hiermee kunt u meer modulaire takenreeksen maken die u opnieuw kunt gebruiken.  

Overweeg het volgende wanneer u een takenreeks onderliggende aan een takenreeks toevoegt.

- De bovenliggende en onderliggende takenreeksen effectief worden gecombineerd tot een enkele beleidsregel die de client wordt uitgevoerd.
- Toevoegen van een onderliggende takenreeks dat een bovenliggend item van een andere takenreeks wordt niet ondersteund.
- De omgeving is wereldwijd. Bijvoorbeeld als een variabele is ingesteld door de bovenliggende takenreeks en vervolgens gewijzigd door de onderliggende takenreeks, de variabele blijft gewijzigd verplaatsen sturen. Op dezelfde manier als de onderliggende takenreeks maakt u een nieuwe variabele, is de variabele beschikbaar voor de resterende stappen in de bovenliggende takenreeks.
- Statusberichten worden voor een enkele takenreeksbewerking per normaal verzonden.
- De takenreeksen vermeldingen schrijven naar het bestand smsts.log met nieuwe logboekbestanden vermeldingen die duidelijk als een onderliggende takenreeks wordt gestart.
- In de Technical Preview voor Configuration Manager, versie 1704, als de onderliggende takenreeksen verwijst naar een pakket en u de bovenliggende takenreeks vanuit Software Center uitvoert, vinden de client niet inhoud van het pakket wanneer de onderliggende takenreeks wordt uitgevoerd. In dit scenario moet u de takenreeks vanaf media uitvoeren (starten, media, PXE, enz.).  

    Als de onderliggende takenreeks maakt gebruik van stappen zoals **opdrachtregel uitvoeren** (zonder een pakket-verwijzing) **indeling**, **BitLocker**, enz., en vervolgens de takenreeks wordt uitgevoerd vanuit Software Center.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Een takenreeks onderliggende toevoegen aan een takenreeks
1. Klik in de takenreekseditor **toevoegen**, selecteer **algemeen**, en klikt u op **Takenreeks uitvoeren**.
2. Klik op **Bladeren** de onderliggende takenreeks selecteren.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>Laden van installatiekopieën voor opstarten met huidige Windows PE-versie
Bij het uitvoeren van **distributiepunten bijwerken** op een geselecteerde opstartinstallatiekopie nu kunt u het laden van de nieuwste versie van Windows PE (van de installatiemap van de Windows ADK) in de installatiekopie. De **algemeen** pagina van de wizard bevat informatie over de Windows ADK-versie op de siteserver, de Windows ADK-versie van die Windows PE is gebruikt in de installatiekopie en de versie van de Configuration Manager-client is geïnstalleerd. U kunt deze informatie gebruiken om te beslissen of u het laden van de opstartinstallatiekopie. Ook een nieuwe kolom (**clientversie**) is toegevoegd wanneer u opstartinstallatiekopieën in de **opstartinstallatiekopieën** knooppunt zodat u weet welke versie van de Configuration Manager-client elke opstartinstallatiekopie wordt gebruikt.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>Laden van een installatiekopie met de huidige versie van Windows PE

1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **opstartinstallatiekopieën**.
2. Een opstartinstallatiekopie selecteren en op **distributiepunten bijwerken**.
3. Op de **algemeen** pagina van de wizard, selecteert u **opnieuw laden installatiekopie met de huidige versie van Windows PE van de geïnstalleerde Windows-ADK**.

## <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
We hebben de volgende verbeteringen in de implementatie van besturingssystemen, die het resultaat van uw stem feedback van gebruikers zijn aangebracht.

- [Nieuwe **versie van het besturingssysteem** kolom voor installatiekopieën van besturingssystemen](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): Hebben we een nieuwe kolom met de naam toegevoegd **versie van het besturingssysteem** voor het weergeven van de versie van het besturingssysteem voor de afbeelding als u informatie bekijken in de **installatiekopieën van besturingssystemen** en **besturingssysteem bijwerken pakketten** knooppunten. Alleen de versie van de eerste index in de. WIM wordt weergegeven. Ga naar de **Details** tabblad voor de installatiekopie te bekijken besturingssysteemversies voor andere indexen.

- [Efficiënter logboekregistratie in Smsts.log](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): Beginnend in deze versie, zijn we niet meer vermeldingen schrijven naar het bestand smsts.log voor CCM_CIVersionInfo.PolicyID informatie. Voor deze versie mogelijk een groot aantal vermeldingen met deze informatie die moeilijk te meer relevante informatie vinden in het logboekbestand.

