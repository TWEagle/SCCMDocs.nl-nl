---
title: Mogelijkheden in Technical Preview 1611 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1611.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 5e77ebbfd3f3d573d903fe58024a22feb9884e4a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1611 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1611 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    

**Bekende problemen in deze Technical Preview:**   
- ***Vereiste status***: Wanneer u versie 1611 installeert, wordt de algehele status voor vereisten mogelijk weergegeven als geslaagd is met waarschuwingen, maar niet wordt vermeld in welke vereisten de waarschuwing heeft veroorzaakt. Dit kan worden veroorzaakt door de volgende twee onderdelen:
  - Opties voor SQL-Index maken geheugen
  - Controleert op een ondersteunde versie van SQL Server  

 Omdat deze alleen waarschuwingen zijn, kunnen ze worden genegeerd.

- ***PowerShell***: Als u verbinding met Windows PowerShell uit de Configuration Manager-console maakt, krijgt u mogelijk de volgende fout: **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml niet digitaal is ondertekend**.  

   U kunt dit probleem oplossen door bepaalde bestanden met ondertekende versies van versie 1610 vervangen. Kopieer alle bestanden met de volgende extensies van de **&lt;installatiemap > \AdminConsole\bin\**  in uw installatie versie 1610: **.psd1**, **.ps1xml**, en **.psm1**. Plak deze bestanden in de **&lt;installatiemap > \AdminConsole\bin\**  in uw technische Preview 1611-installatie, de 1611-versie van de bestanden worden overschreven.


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Vooraf cache-inhoud voor beschikbare implementaties en takenreeksen
In dit voorbeeld technische voor beschikbare implementaties en takenreeksen, kunt u de vooraf cachefunctie gebruiken zodat clients alleen relevante inhoud worden gedownload voordat een gebruiker de inhoud wordt geïnstalleerd.

Stel dat u wilt implementeren van een Windows-10 in-place upgrade takenreeks alleen een enkele takenreeks wilt gebruiken voor alle gebruikers en meerdere architecturen en/of talen. In huidige filiaal, als u een beschikbare installatie maakt en vervolgens de gebruiker **installeren** in Software Center, de inhoud gedownload op dat moment. Hiermee voegt u extra tijd voordat de installatie is gereed om te beginnen. U kunt ook in de huidige vertakking wordt als u een beschikbare takenreeksimplementatie alle inhoud waarnaar wordt verwezen in de takenreeks gedownload. Dit omvat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als elk ongeveer 3 GB groot zijn is, kan het downloadpakket behoorlijk groot zijn.

De inhoud vooraf cachefunctie biedt u de optie om de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

### <a name="to-configure-the-pre-cache-feature"></a>De vooraf cachefunctie configureren

1. Upgradepakketten voor specifieke architecturen en talen voor besturingssysteem maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal (bijvoorbeeld 1033 is het decimaalteken voor Engels en 0x0409 is het hexadecimale equivalent). Zie voor meer informatie, [maken van een takenreeks om een besturingssysteem te upgraden](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    De architectuur en taal-waarden worden gebruikt om te voldoen aan de taak volgorde stap die u in de volgende stap om te bepalen maakt of het upgradepakket voor besturingssysteem vooraf moet worden opgeslagen.
2. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. U kunt bijvoorbeeld een stap in de volgende notatie maken voor de Engelse versie:

    ![vooraf cache-eigenschappen](media/precacheproperties2.png)

    ![vooraf cacheopties](media/precacheoptions2.png)  

3. De takenreeks implementeert. Voor de functie cache voorafgaand aan het volgende configureren:
    - Op de **algemeen** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureert u de takenreeks met de **beschikbaar** voor **doel**. Als u een **vereist** implementatie van de vooraf cache-functionaliteit werkt niet.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** stellen, een tijdstip in de toekomst waarmee clients voldoende tijd om de inhoud vooraf in cache voordat de implementatie beschikbaar wordt gesteld aan gebruikers te kiezen. U kunt bijvoorbeeld de hoeveelheid tijd moet drie uur in de toekomst genoeg tijd bieden om de inhoud vooraf in cache opgeslagen instellen.  
    - Op de **distributiepunten** tabblad, configureert u de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache op een client opgeslagen is voordat een gebruiker de installatie wordt gestart, worden deze instellingen gebruikt.


### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, start het vooraf om de inhoud in cache. Dit omvat alle inhoud waarnaar wordt verwezen (een andere pakkettypen) en alleen de upgradepakket besturingssysteem die overeenkomt met de client op basis van de voorwaarden in de takenreeks te stellen.
- Wanneer de implementatie beschikbaar wordt gesteld aan gebruikers (instellen op de **planning** tabblad van de implementatie), een melding wordt weergegeven om gebruikers te informeren over de nieuwe implementatie en de implementatie wordt weergegeven in Software Center. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is, worden de instellingen op de instellingen wilt gebruiken de **Implementatieoptie** tabblad van de implementatie. U wordt aangeraden dat er voldoende tijd tussen wanneer de implementatie wordt gemaakt en het tijdstip waarop de implementatie beschikbaar voor gebruikers wordt wilt toestaan dat clients voldoende tijd om de inhoud vooraf in cache is.


## <a name="see-also"></a>Zie ook
[Technische Preview van System Center Configuration Manager](../../core/get-started/technical-preview.md)

