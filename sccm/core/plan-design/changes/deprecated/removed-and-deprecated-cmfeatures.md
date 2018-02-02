---
title: Voor Configuration Manager-functies afgeschaft
titleSuffix: Configuration Manager
description: Meer informatie over de functies die niet langer ondersteuning biedt voor System Center Configuration Manager.
ms.custom: na
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 287a6324-ae65-4d38-b2ef-198d47c91231
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: d49e0f839106af652f7b49227b6c4f8c957347d9
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Verwijderde en afgeschafte functies voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit artikel beschrijft de functies die worden verwijderd van ondersteuning voor System Center Configuration Manager of wordt verwijderd in een toekomstige update (afgeschaft). Dit artikel bevat vroege kennisgeving over toekomstige wijzigingen die invloed kunnen zijn op uw gebruik van Configuration Manager.  

Deze informatie kan worden gewijzigd in toekomstige versies, en bevat mogelijk niet alle afgeschafte functies voor Configuration Manager.

## <a name="deprecated-features"></a>Afgeschafte functies  

|**Functie**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd**|  
|-|-|-|  
|Met de komst van de nieuwe ervaring met Software Center in versie 1511 weergegeven apps die nu alleen in de Toepassingscatalogus (voor gebruikers beschikbare apps eerst) in Software Center. </br></br>Met deze primaire functionaliteit van de Application Catalog nu opgenomen in Software Center kan wordt de Application Catalog webgebaseerde ervaring niet langer beschikbaar in de komende maanden.|11 augustus 2017| Ondersteuning voor de Application Catalog website gebruikerservaring op de eerste update die na 1 juni 2018 wordt uitgebracht eindigt|
|Software Center heeft een nieuwe, moderne vormgeving. In de komende maanden wordt de vorige versie van het Software Center niet langer beschikbaar.<br><br>U kunt clients zo instellen dat er gebruik van het nieuwe Software Center doordat de client-instelling, **Computeragent** > **nieuwe Software Center gebruiken**.<br><br>Zie voor meer informatie over Software Center [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|December 13 mei 2016|Ondersteuning voor de vorige versie van Software Center eindigt met de eerste update die na 1 januari 2018 uitgebracht.|
|Beheer van virtuele harde schijven (VHD's) met Configuration Manager. </br></br>Dit omvat het verwijderen van de opties voor een nieuwe VHD maken of beheren van een VHD met behulp van een takenreeks en het verwijderen van het knooppunt van de virtuele harde schijven uit de Configuration Manager-console. </br></br>Wanneer deze ondersteuning wordt verwijderd, worden bestaande VHD's worden niet verwijderd, maar niet langer toegankelijk vanuit de Configuration Manager-console.  |6 januari 2017 |Versie 1710|
|Takenreeksen: <br /> -Schijf naar dynamische schijf converteren <br /> -Implementatiehulpprogramma's installeren |18 november 2016|Versie 1710|
|System Center Configuration Manager Upgrade Assessment Tool. </br></br>Het hulpprogramma Upgradebeoordeling hangt af van System Center Configuration Manager en Application Compatibility Toolkit (ACT) 6.x. De definitieve versie van ACT is geleverd in de v1511 Windows 10 ADK. Omdat er wordt geen verdere updates met de functioneren, ondersteuning voor het hulpprogramma Upgradebeoordeling stopgezet. </br></br>Het hulpprogramma Upgradebeoordeling wordt vervangen door de [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) functie. Afschaffing bericht is toegevoegd aan de [downloadpagina voor UAT](https://www.microsoft.com/download/details.aspx?id=37145) op 12 September 2016. | Op 12 september 2016  | 11 juli 2017 |
|Takenreeksen: <br /> - OSDPreserveDriveLetter  <br /><br /> Tijdens de implementatie van een besturingssysteem bepaalt standaard Windows Setup nu de beste stationsletter te gebruiken (meestal C:). Als u opgeven van een ander station moet worden gebruikt wilt, kunt u de locatie van de takenreeksstap besturingssysteem toepassen. Ga naar de **selecteert u de locatie waar u wilt toepassen van dit besturingssysteem** instelling. Selecteer **logische stationsletter opgeven** en kies het station dat u wilt gebruiken. |20 juni 2016 |Versie 1606 |
|Network Access Protection (NAP) – zoals gevonden in System Center 2012 Configuration Manager|10 juli 2015|Versie 1511|  
|Buiten-Bandbeheer – zoals gevonden in System Center 2012 Configuration Manager|16 oktober 2015|Versie 1511|



<br></br>
Aanvullende details voor onderdelen met versie 1511 van System Center Configuration Manager release verwijderd:

###  <a name="bkmk_amt"></a>Buiten-Bandbeheer  
 Met Configuration Manager systeemeigen ondersteuning voor AMT-gebaseerde computers uit binnen de Configuration Manager-console is verwijderd.  

-   AMT-gebaseerde computers blijven volledig beheerd wanneer u de [Intel SCS-invoegtoepassing voor Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). De invoegtoepassing biedt dat u toegang tot de nieuwste mogelijkheden voor het beheer van AMT terwijl beperkingen die zijn geïntroduceerd totdat Configuration Manager deze wijzigingen kon opvangen worden weggenomen.  

-   Buiten-Bandbeheer in System Center 2012 Configuration Manager wordt niet beïnvloed door deze wijziging.  

###  <a name="bkmk_nap"></a>Network Access Protection  
 System Center Configuration Manager heeft ondersteuning voor Network Access Protection verwijderd. De functie is afgeschaft in Windows Server 2012 R2 en wordt uit Windows 10 verwijderd.  

 Bekijk het gedeelte *Afgeschafte functionaliteit* van [Overzicht van Services voor netwerkbeleid en -toegang](https://technet.microsoft.com/library/hh831683.aspx) voor informatie over alternatieven voor netwerktoegangsbeveiliging.

## <a name="more-information"></a>Meer informatie
Zie voor meer informatie:
 - [Verwijderde en afgeschafte](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - De [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle) website.
 - [Ondersteuning voor de huidige vertakking versies van Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).
