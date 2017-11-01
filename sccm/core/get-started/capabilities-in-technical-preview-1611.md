---
title: Mogelijkheden van Technical Preview 1611
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1611.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: c97143f5141268e041a6685f58f3c77402098ba4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1611 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1611 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    

**Bekende problemen in deze Technical Preview:**   
- ***De status van vereisten***: Wanneer u versie 1611 installeert, worden de algehele status voor vereiste onderdelen mogelijk weergegeven omdat het is voltooid met waarschuwingen, maar niet wordt vermeld welke vereisten de waarschuwingen veroorzaakt. Dit kan zijn veroorzaakt door de volgende twee vereisten:
  - Opties voor het SQL-Index maken-geheugen
  - Controleert op een ondersteunde versie van SQL Server  

 Omdat dit alleen waarschuwingen zijn, kunnen ze worden genegeerd.

- ***PowerShell***: Als u verbinding met Windows PowerShell uit de Configuration Manager-console, kunt u de volgende fout ontvangen: **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml niet digitaal is ondertekend**.  

   U kunt dit probleem oplossen door het vervangen van bepaalde bestanden met ondertekende versies van versie 1610. Kopieer alle bestanden met de volgende extensies van de **&lt;installatiemap > \AdminConsole\bin\**  map in de installatie van versie 1610: **.psd1**, **.ps1xml**, en **.psm1**. Plak deze bestanden in de **&lt;installatiemap > \AdminConsole\bin\**  map in de installatie van Technical Preview 1611, wordt de 1611-versie van de bestanden overschreven.


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Vooraf cache-inhoud voor beschikbare implementaties en takenreeksen
In deze technical preview voor beschikbare implementaties en takenreeksen, kunt u de functie vooraf cache gebruiken om clients alleen relevante inhoud downloaden voordat een gebruiker de inhoud installeert hebben.

Stel dat u wilt implementeren van een takenreeks Windows 10 in-place upgrade slechts een enkele takenreeks voor alle gebruikers wilt en meerdere architecturen en/of talen. In huidige vertakking, als u een beschikbare installatie maakt, en vervolgens klikt de gebruiker op **installeren** in Software Center, de inhoud gedownload op dat moment. Hiermee voegt u extra tijd voordat de installatie is gereed om te starten. U kunt ook in huidige vertakking wordt als u een beschikbare takenreeksimplementatie maakt alle inhoud waarnaar wordt verwezen in de takenreeks gedownload. Dit omvat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als elk ongeveer 3 GB groot is, kan het downloadpakket behoorlijk groot zijn.

De inhoud vooraf cachefunctie biedt u de optie voor het toestaan van de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker klikt op **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

### <a name="to-configure-the-pre-cache-feature"></a>De cachefunctie vooraf configureren

1. Upgradepakketten voor specifieke architecturen en talen voor besturingssysteem maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal (bijvoorbeeld 1033 is het decimaalteken voor Engels en 0x0409 is hetzelfde als hexadecimaal). Zie voor meer informatie [een takenreeks maken om een besturingssysteem te upgraden](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    De architectuur en taal-waarden worden gebruikt om te voldoen aan de taak sequence stap die u in de volgende stap om te bepalen maakt of het upgradepakket voor besturingssysteem vooraf moet worden opgeslagen.
2. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. U kunt bijvoorbeeld een stap als volgt maken voor de Engelse versie:

    ![Eigenschappen van de pre-cache](media/precacheproperties2.png)

    ![vooraf cacheopties](media/precacheoptions2.png)  

3. De takenreeks implementeert. Voor de functie vooraf cache, het volgende configureren:
    - Op de **algemene** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureer de takenreeks met de **beschikbaar** voor **doel**. Als u maakt een **vereist** implementatie van de pre-cache-functionaliteit werkt niet.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** instelt, kiest u een tijd in de toekomst waarmee clients voldoende tijd is voor de inhoud vooraf in cache voordat de implementatie beschikbaar wordt gesteld aan gebruikers. U kunt bijvoorbeeld instellen dat de beschikbare tijd worden drie uur in de toekomst genoeg tijd bieden om de inhoud vooraf in cache opgeslagen.  
    - Op de **distributiepunten** tabblad, configureert de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache op een client opgeslagen is voordat een gebruiker de installatie wordt gestart, worden deze instellingen gebruikt.


### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, wordt gestart om de inhoud vooraf in cache. Dit omvat alle inhoud waarnaar wordt verwezen (een andere typen) en alleen het upgradepakket voor besturingssysteem die overeenkomt met de client op basis van de voorwaarden die u in de takenreeks instelt.
- Wanneer de implementatie wordt beschikbaar gesteld aan gebruikers (instellen op de **planning** tabblad van de implementatie), een melding weergegeven om gebruikers te informeren over de nieuwe implementatie en de implementatie zichtbaar in Software Center. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is, wordt dit de instellingen gebruikt van de **Implementatieoptie** tabblad van de implementatie. U wordt aangeraden dat er voldoende tijd tussen wanneer de implementatie wordt gemaakt en het tijdstip waarop de implementatie beschikbaar voor gebruikers wordt wilt toestaan dat clients voldoende tijd is voor de inhoud vooraf in cache is.


## <a name="see-also"></a>Zie ook
[Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md)
