---
title: Technische Preview 1711 | Microsoft Docs
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1711 voor System Center Configuration Manager.
ms.custom: na
ms.date: 11/17/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e68dc12-6776-437a-9138-45cd7d4bf9cf
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: b740c422a71e625ccc110a043028cf986cdffb20
ms.sourcegitcommit: ed8b2438ef85c9160741ef61f9171be41dd1ae0a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/17/2017
---
# <a name="capabilities-in-technical-preview-1711-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1711 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1711 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Bekende problemen in deze Technical Preview:**
-   **Ondersteuning voor Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update)**.  Vanaf deze versie van Windows, bevat Windows media meerdere edities. Bij het configureren van een takenreeks om een upgradepakket voor besturingssysteem of de installatiekopie van besturingssysteem te gebruiken, moet u selecteren een [-editie die wordt ondersteund voor gebruik door Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).
-   **Bijwerken naar een nieuwe preview-versie mislukt wanneer u een siteserver in de passieve modus hebt**. Wanneer u een preview-versie uitvoert die heeft een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), moet u de passieve modus siteserver verwijderen voordat u de preview-site met succes naar deze nieuwe preview-versie bijwerken kunt. Nadat de site de update is voltooid, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de console naar **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster, rechts Klik op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-to-run-task-sequence"></a>Verbeteringen in de Takenreeks uitvoeren
<!-- 1261338 -->

Deze technical preview verbeteren van de stap van de Takenreeks worden uitgevoerd. Verbeteringen bestaan onder andere de volgende items:

 - Ondersteuning voor alle implementatiescenario's van besturingssysteem vanuit Software Center, PXE en media.
 - Verbeteringen in de console acties zoals kopiëren, import, export en waarschuwing tijdens het verwijderen van objecten.
 - Ondersteuning voor de **voorbereid inhoud maken** wizard.
 - Integratie met implementatieverificatie.
 - De Takenreeks uitvoeren stap kan nu worden gebruikt op meerdere niveaus van takenreeksen, niet alleen een één-bovenliggende / onderliggende relatie. Met meerdere niveaus relaties verhogen van de complexiteit, dus wees voorzichtig. Deze relaties worden nog steeds gecontroleerd voor kringverwijzingen bevatten.

### <a name="try-it-out"></a>Probeer het nu!  

Voer de volgende taken en klikt u vervolgens Stuur ons **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:

1. Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en klik op **Takenreeks uitvoeren**.
2. Klik op **Bladeren** naar de onderliggende takenreeks selecteren.

## <a name="allow-user-interaction-when-installing-an-application----1356976---"></a>Interactie van de gebruiker toestaan bij het installeren van een toepassing<!-- 1356976 -->

Met deze preview kunt u een eindgebruiker om te communiceren met de installatie van een toepassing tijdens het uitvoeren van de takenreeks. Bijvoorbeeld: een setup-proces dat wordt de eindgebruiker gevraagd voor verschillende opties uitvoeren. Sommige installatieprogramma van de toepassing geen gebruikersvragen onderdrukt of het installatieproces moet u mogelijk specifieke configuratiewaarden alleen bekend is dat de gebruiker. Deze functie kunt u deze installatie-scenario's te verwerken.

### <a name="try-it-out"></a>Probeer het nu!

Voer de volgende taken en verzend **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:

1.  Maken of bewerken van een toepassing. Zie voor meer informatie [toepassingen maken met System Center Configuration Manager](/sccm/apps/deploy-use/create-applications).

    a. Kies de **gebruikerservaring** tabblad de **Windows Installer (\*msi-bestand) eigenschappen**.

    b. Selecteer **installeren voor systeem** voor **installatiegedrag**.

    c. Selecteer **al dan niet een gebruiker is aangemeld** voor **Meld u aan de vereiste**.

    d. Selecteer **normaal** voor **zichtbaarheid installatieprogramma**. U kunt kiezen uit drie opties: **Geminimaliseerd**, **normaal**, of **gemaximaliseerd**.

    e. Selecteer de **gebruikers kunnen communiceren met de programma-installatie** vak.

2.  Maken of bewerken van een takenreeks voor het installeren van de toepassing met behulp van de **toepassing installeren** stap. Zie voor meer informatie [toepassing installeren](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication) in de [takenreeksstappen in System Center Configuration Manager](/sccm/osd/understand/task-sequence-steps).

    a. Installatiekopieën van de takenreeks na de stap Windows en Configuration Manager.

    b. In-place upgrade takenreeks in de groep na verwerking.

3.  Implementeer de takenreeks op een client.
4.  De takenreeks installeren vanuit Software Center.

Tijdens de voortgang van de takenreeks verschijnt de interface van de installatie van toepassing op het doelapparaat door eindgebruikers. De voortgang van de takenreeks wordt onderbroken totdat de gebruiker de werkstroom van de installatie van toepassing is voltooid.

### <a name="install-using-the-wizard"></a>Installeren met behulp van de wizard

U kunt deze functie ook gebruiken bij het implementeren van een app met de wizard.

1. Maken of bewerken van een toepassing.
2. Implementeer de toepassing naar een client.
3. De toepassing installeren vanuit Software Center. De interface van de installatie van toepassing moet worden weergegeven. De eindgebruiker moet Volg de installatiewizard van de toepassing en de toepassing is geïnstalleerd.




<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
