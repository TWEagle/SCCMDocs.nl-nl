---
title: Afgeschafte functies | Microsoft Docs
description: Meer informatie over de functies, producten en besturingssystemen die niet langer ondersteuning biedt voor System Center Configuration Manager.
ms.custom: na
ms.date: 08/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: "15"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8ac7009014a4652a36acf69ebfe9ccab3ba8ecbd
ms.sourcegitcommit: 3ce56c7350411d8cc3d3cb9b4054f9ada9b0ed54
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/17/2017
---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Verwijderde en afgeschafte functies voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp beschrijft de functies, producten en besturingssystemen die worden verwijderd van ondersteuning voor System Center Configuration Manager of wordt verwijderd in een toekomstige update (afgeschaft). Dit biedt vroege kennisgeving over toekomstige wijzigingen die invloed kunnen zijn op uw gebruik van Configuration Manager.  

Deze informatie kan worden gewijzigd in toekomstige versies, en bevat mogelijk niet alle afgeschafte functies, producten of besturingssysteem.  

## <a name="how-to-use-this-information"></a>Het gebruik van deze informatie  
Wanneer een functie of het besturingssysteem eerst weergegeven wordt als afgeschaft, wordt ondersteuning voor het gebruik ervan met Configuration Manager gepland om te worden verwijderd uit toekomstige versies van Configuration Manager. Deze informatie wordt verstrekt om te plannen voor alternatieven voor het gebruik van deze functie of het besturingssysteem. Wanneer de eerste versie van Configuration Manager versies in welke waarmee ondersteuning wordt verwijderd, wordt dit onderwerp is bijgewerkt om aan te geven die specifieke versie.  

Als u ondersteuning voor een functie of het besturingssysteem wordt verwijderd, blijft de functie of het besturingssysteem ondersteund wanneer u een eerdere versie van Configuration Manager gebruikt, zolang die versie van Configuration Manager in de ondersteuning blijft. Echter, wanneer u een versie van Configuration Manager, vrijgegeven na de datum of aangegeven, die versie van Configuration Manager biedt geen ondersteuning.

Bijvoorbeeld als een functie is gepland om de ondersteuning verwijderd met zou de eerste update die na September 2016, ondersteuning voor deze functie wordt uitgebracht niet langer worden opgenomen in update 1610, in oktober 2016 uitgebracht.
-  Met Update 1610, zou u de functie niet meer ondersteund.
-  In dit onderwerp zou worden bijgewerkt om aan te geven ondersteuning met versie 1610 is verwijderd.
Echter, als u blijven gebruiken van een eerdere versie die ondersteuning biedt voor de functie, zoals versie 1602 of 1606, kunt u blijven die functie te gebruiken, pas de versie die u gebruikt niet worden ondersteund.

Zie voor meer informatie:
 - De [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle) website.
 - [Ondersteuning voor de huidige vertakking versies van Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).




## <a name="deprecated-operating-systems"></a>Afgeschafte besturingssystemen
### <a name="server-operating-systems"></a>Server-besturingssystemen  

|**Besturingssystemen**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd** |  
|-|-|-|  
|Windows Server 2008|10 juli 2015|Versie 1511 </br></br>Ondersteuning voor een sitesysteem is verwijderd. (Zie Opmerking 1).|  
|Windows Server 2008 R2|10 juli 2015| Versie 1702 (Zie Opmerking 2)|  

-   Opmerking 1: Dit besturingssysteem wordt niet ondersteund voor siteservers of sitesysteemrollen met uitzondering van het distributiepunt en pull-distributiepunt. U kunt blijven gebruiken van dit besturingssysteem als een distributiepunt totdat afschaffing van deze ondersteuning wordt aangekondigd of de periode voor uitgebreide ondersteuning van dit besturingssysteem is verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

-   Opmerking 2:    Vanaf versie 1702, wordt dit besturingssysteem niet ondersteund voor siteservers of de meeste sitesysteemrollen echter versies voorafgaand aan 1702 blijven ondersteunen het gebruik ervan. Dit besturingssysteem ondersteund voor de sitesysteemrol distributiepunt blijven (inclusief pull-distributiepunten en voor PXE en multicast) totdat afschaffing van deze ondersteuning wordt aangekondigd of van dit besturingssysteem uitgebreide ondersteuning is verstreken. Vanaf versie 1602 kunt u kunt een upgrade ter plekke het besturingssysteem van een siteserver van Windows Server 2008 R2 naar Windows Server 2012 R2.  

     Zie voor meer informatie over in-place upgrade uit van een besturingssysteem van de site-servers, de [In-place upgrade van het besturingssysteem van siteservers waarop Windows Server 2008 R2 uitgevoerd](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) in sectie [wat er veranderd in System Center Configuration Manager](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).



### <a name="client-operating-systems"></a>Client-besturingssystemen  

 Tenzij anders vermeld wordt elk besturingssysteem dat wordt ondersteund als een Configuration Manager-client ondersteund totdat de einddatum uitgebreide ondersteuning van dat besturingssysteem. Zie voor meer informatie over de einddatum voor uitgebreide ondersteuning voor de [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Als Configuration Manager-ondersteuning voor een besturingssysteem wordt beëindigd voordat voor de ondersteuning van einddatum voor uitgebreide, worden afschaffing en beëindiging van de ondersteuning voor dat besturingssysteem hier vermeld.  

|**Besturingssystemen**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd**|  
|-|-|-|  
|Windows XP|10 juli 2015|Versie 1511|  
|Windows XP Embedded <br><br> Dit omvat alle [XP gebaseerde ingesloten besturingssystemen](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#windows-embedded-computers).|10 juli 2015|Versie 1702|  
|Windows Server 2003|10 juli 2015|Versie 1511|  
|Windows Server 2003 R2|10 juli 2015|Versie 1511|  
|Windows Vista|10 juli 2015|Versie 1511|  
|Mac OS X 10.6 10.8|10 juli 2015|Versie 1511|  
|Windows Mobile 6.0 6.5|10 juli 2015|Versie 1511|  
|Nokia Symbian Belle|10 juli 2015|Versie 1511|  
|Windows CE 5.0 6.0|10 juli 2015|Versie 1511|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Afgeschafte ondersteuning voor versies van SQL Server als een sitedatabase  

|**SQL Server-versies**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd**|   
|-|-|-|  
|SQL Server 2008|10 juli 2015|Versie 1511|  
|SQL Server 2008 R2|10 juli 2015|Versie 1702|  

Als u moet de versie van SQL Server wilt bijwerken, raden wij de volgende methoden van eenvoudig complexere.
1. [SQL Server in-place upgrade](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (aanbevolen).
2. Een nieuwe versie van SQL Server op een nieuwe computer installeren en vervolgens [gebruikt u de optie-database verplaatsen](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) installatieprogramma van Configuration Manager uw siteserver verwijzen naar de nieuwe SQL-Server.
3. Gebruik [back-up en herstel](/sccm/protect/understand/backup-and-recovery).


## <a name="deprecated-features"></a>Afgeschafte functies  

|**Functie**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd**|  
|-|-|-|  
|Network Access Protection (NAP) – zoals gevonden in System Center 2012 Configuration Manager|10 juli 2015|Versie 1511|  
|Buiten-Bandbeheer – zoals gevonden in System Center 2012 Configuration Manager|16 oktober 2015|Versie 1511|
|Takenreeksen: <br /> -OSDPreserveDriveLetter  <br /><br /> Tijdens de implementatie van een besturingssysteem bepaalt standaard Windows Setup nu de beste stationsletter te gebruiken (meestal C:). Als u opgeven van een ander station moet worden gebruikt wilt, kunt u de locatie van de takenreeksstap besturingssysteem toepassen. Ga naar de **selecteert u de locatie waar u wilt toepassen van dit besturingssysteem** optie **logische stationsletter opgeven**, en kies het station dat u wilt gebruiken. |20 juni 2016 |Versie 1606 |
|Takenreeksen: <br /> -Schijf naar dynamische schijf converteren <br /> -Implementatiehulpprogramma's installeren |18 november 2016|Ondersteuning voor deze taak takenreeksen eindigt met de eerste update die na 1 juni 2017 uitgebracht.|
|Software Center heeft een nieuwe, moderne vormgeving. In de komende maanden wordt de vorige versie van het Software Center niet langer beschikbaar.<br><br>U kunt clients zo instellen dat er gebruik van het nieuwe Software Center doordat de client-instelling, **Computeragent** > **nieuwe Software Center gebruiken**.<br><br>Zie voor meer informatie over Software Center [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|December 13 mei 2016|Ondersteuning voor de vorige versie van Software Center eindigt met de eerste update die na 1 januari 2018 uitgebracht.|
|Met de komst van de nieuwe ervaring met Software Center in versie 1511 weergegeven apps die nu alleen in de Toepassingscatalogus (voor gebruikers beschikbare apps eerst) in Software Center. </br></br>Met deze primaire functionaliteit van de Application Catalog nu opgenomen in Software Center kan wordt de Application Catalog webgebaseerde ervaring niet langer beschikbaar in de komende maanden.|11 augustus 2017| Ondersteuning voor de Application Catalog website gebruikerservaring op de eerste update die na 1 juni 2018 wordt uitgebracht eindigt|
|Beheer van virtuele harde schijven (VHD's) met Configuration Manager. </br></br>Dit omvat het verwijderen van de opties voor een nieuwe VHD maken of beheren van een VHD met behulp van een takenreeks en het verwijderen van het knooppunt van de virtuele harde schijven uit de Configuration Manager-console. </br></br>Wanneer deze ondersteuning wordt verwijderd, worden bestaande VHD's worden niet verwijderd, maar niet langer toegankelijk vanuit de Configuration Manager-console.  |6 januari 2017 |Ondersteuning voor virtuele harde schijven eindigt met de eerste update die na 1 juni 2017 uitgebracht.|
|System Center Configuration Manager Upgrade Assessment Tool. </br></br>Het hulpprogramma Upgradebeoordeling hangt af van System Center Configuration Manager en Application Compatibility Toolkit (ACT) 6.x. De definitieve versie van ACT is geleverd in de v1511 Windows 10 ADK. Omdat er wordt geen verdere updates met de functioneren, ondersteuning voor het hulpprogramma Upgradebeoordeling stopgezet. </br></br>Het hulpprogramma Upgradebeoordeling wordt vervangen door de [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) functie. Afschaffing bericht is toegevoegd aan de [downloadpagina voor UAT](https://www.microsoft.com/download/details.aspx?id=37145) op 9-12-2016. |9/12/2016  | 11 juli 2017 |


<br></br>
Aanvullende details voor onderdelen met versie 1511 van System Center Configuration Manager release verwijderd:

###  <a name="bkmk_amt"></a>Buiten-Bandbeheer  
 Met Configuration Manager systeemeigen ondersteuning voor AMT-gebaseerde computers uit binnen de Configuration Manager-console is verwijderd.  

-   AMT-gebaseerde computers blijven volledig beheerd wanneer u de [Intel SCS-invoegtoepassing voor Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). De invoegtoepassing biedt dat u toegang tot de nieuwste mogelijkheden voor het beheer van AMT terwijl beperkingen die zijn geïntroduceerd totdat Configuration Manager deze wijzigingen kon opvangen worden weggenomen.  

-   Buiten-Bandbeheer in System Center 2012 Configuration Manager wordt niet beïnvloed door deze wijziging.  

###  <a name="bkmk_nap"></a>Network Access Protection  
 System Center Configuration Manager heeft ondersteuning voor Network Access Protection verwijderd. De functie is afgeschaft in Windows Server 2012 R2 en wordt uit Windows 10 verwijderd.  

 Bekijk het gedeelte *Afgeschafte functionaliteit* van [Overzicht van Services voor netwerkbeleid en -toegang](https://technet.microsoft.com/library/hh831683.aspx) voor informatie over alternatieven voor netwerktoegangsbeveiliging.
