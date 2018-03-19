---
title: Clientstatus configureren
titleSuffix: Configuration Manager
description: Selecteer de status van clientinstellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2275ba2-c83d-43e7-90ed-418963a707fe
caps.latest.revision: 
caps.handback.revision: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5db52925515e65797a43ed35775460369f742f49
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-configure-client-status-in-system-center-configuration-manager"></a>Clientstatus configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u kunt de status van de System Center Configuration Manager-client controleren en oplossen van problemen die zijn gevonden, moet u uw site om op te geven van de parameters die worden gebruikt voor clients als inactief markeren en opties configureren zodat u wordt gewaarschuwd als de clientactiviteiten onder een bepaalde drempelwaarde vallen. U kunt ook voorkomen automatisch oplossen van problemen die door clientstatus worden gevonden.  

##  <a name="BKMK_1"></a>Clientstatus configureren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte, klikt u op **clientstatus**, klik op de **Start** tabblad, in de **clientstatus** groep, klikt u op **Clientstatusinstellingen**.  

3.  In de **eigenschappen van Clientstatusinstellingen** dialoogvenster geeft u de volgende waarden om te bepalen van clientactiviteit:  

    > [!NOTE]  
    >  Als geen van de instellingen wordt voldaan, wordt de client als inactief worden gemarkeerd.  

    -   **Clientbeleidsaanvragen gedurende de volgende dagen:** Geef het aantal dagen geleden een client beleid heeft aangevraagd. De standaardwaarde is **7** dagen.  

    -   **Heartbeat-detectie gedurende de volgende dagen:** Geef het aantal dagen geleden de clientcomputer een hartslagdetectierecord naar de sitedatabase verzonden. De standaardwaarde is **7** dagen.  

    -   **Hardware-inventarisatie gedurende de volgende dagen:** Geef het aantal dagen geleden de clientcomputer een hardware-inventarisatierecord naar de sitedatabase heeft verzonden. De standaardwaarde is **7** dagen.  

    -   **Software-inventarisatie gedurende de volgende dagen:** Geef het aantal dagen geleden de clientcomputer een software-inventarisatierecord naar de sitedatabase heeft verzonden. De standaardwaarde is **7** dagen.  

    -   **Statusberichten gedurende de volgende dagen:** Geef het aantal dagen geleden de clientcomputer statusberichten naar de sitedatabase heeft verzonden. De standaardwaarde is **7** dagen.  

4.  In de **eigenschappen van Clientstatusinstellingen** dialoogvenster geeft u de volgende waarde om te bepalen hoe lang historische gegevens voor de client worden bewaard:  

    -   **Geschiedenis van clientstatus bewaren gedurende het volgende aantal dagen:** Geef op hoe lang de geschiedenis van clientstatus blijven in de sitedatabase. De standaardwaarde is **31** dagen.  

5.  Klik op **OK** de eigenschappen op te slaan en sluit de **eigenschappen van Clientstatusinstellingen** in het dialoogvenster.  

##  <a name="BKMK_Schedule"></a>De planning voor de clientstatus configureren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte, klikt u op **clientstatus**, klik op de **Start** tabblad, in de **clientstatus** groep, klikt u op **Clientstatusupdate**.  

3.  In de **Clientstatusupdate** dialoogvenster Configureer het interval waarmee u de clientstatus wilt bijwerken en klik vervolgens op OK.  

    > [!NOTE]  
    >  Wanneer u de planning voor clientstatusupdates wijzigt, worden de update pas van kracht totdat de volgende geplande clientstatusupdate (voor de eerder geconfigureerde planning).  

##  <a name="BKMK_2"></a>Waarschuwingen voor de clientstatus configureren  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.  

3.  Selecteer in de lijst **Apparaatverzamelingen** de verzameling waarvoor u waarschuwingen wilt configureren en klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

    > [!NOTE]  
    >  U kunt geen waarschuwingen voor gebruikersverzamelingen configureren.  

4.  Op de **waarschuwingen** tabblad van de  *&lt;verzameling naam\>***eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.  

    > [!NOTE]  
    >  Het tabblad **Waarschuwingen** is alleen zichtbaar als aan de beveiligingsrol waaraan u gekoppeld bent machtigingen voor waarschuwingen zijn toegewezen.  

5.  Geef in het dialoogvenster **Nieuwe verzamelingmeldingen toevoegen** op welke meldingen moeten worden gegenereerd wanneer clientstatuswaarden onder een bepaalde drempelwaarde vallen en klik vervolgens op **OK**.  

6.  Selecteer elke clientstatuswaarschuwing in de lijst **Voorwaarden** van het tabblad **Waarschuwingen** en geef vervolgens de volgende gegevens op.  

    -   **Naam melding** : Accepteer de standaardnaam of voer een nieuwe naam voor de waarschuwing.  

    -   **Ernst melding** - Selecteer in de vervolgkeuzelijst de ernst die moet worden weergegeven in de Configuration Manager-console.  

    -   **Waarschuwing activeren** -Geef het drempelwaardepercentage voor de waarschuwing.  

7.  Klik op **OK** sluiten de  *&lt;verzameling naam\>***eigenschappen** in het dialoogvenster.  

##  <a name="BKMK_3"></a>Computers uitsluiten van automatisch herstel  

1.  Open de Register-editor op de clientcomputer waarvoor u wilt uitschakelen van automatisch herstel.  

    > [!WARNING]  
    >  Als u de Register-Editor onjuist gebruikt, kunt u ernstige problemen waarvoor u het besturingssysteem opnieuw installeren kunnen veroorzaken. Microsoft biedt geen garantie dat u problemen kunt oplossen die veroorzaakt worden door onjuist gebruik van de Registry Editor. Gebruik de Registry Editor op eigen risico.  

2.  Navigeer naar **HKEY_LOCAL_MACHINE\Software\Microsoft\CCM\CcmEval\NotifyOnly**.  

3.  Voer een van de volgende waarden voor deze registersleutel:  

    -   **De waarde True** -eventuele problemen die zijn gevonden worden niet automatisch hersteld door de clientcomputer. Echter, wordt u nog wel gewaarschuwd de **bewaking** werkruimte over eventuele problemen met deze client.  

    -   **ONWAAR** -problemen worden automatisch door de clientcomputer worden hersteld wanneer ze zijn gevonden en u wordt gewaarschuwd in de **bewaking** werkruimte. Dit is de standaardinstelling.  

4.  Sluit de Register-editor.  

 U kunt clients ook installeren met de CCMSetup **NotifyOnly** installatie-eigenschap ze uitsluiten van automatisch herstel. Zie voor meer informatie over deze clientinstallatie-eigenschap [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  
