---
title: Afgeschafte functies | Microsoft-documenten
description: Meer informatie over de functies, producten en besturingssystemen die System Center Configuration Manager biedt geen ondersteuning meer.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d8c8b44c-1e8a-42b6-bab4-23c72a0a6169
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 57b9ab13bda0bb5fa5139e52a4c55ef9524e4097
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="removed-and-deprecated-features-for-system-center-configuration-manager"></a>Verwijderde en afgeschafte functies voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp beschrijft de functies, producten en besturingssystemen die worden verwijderd uit de ondersteuning voor System Center Configuration Manager, of wordt verwijderd in een toekomstige update (afgeschaft). Dit biedt vroegtijdige kennisgeving over toekomstige wijzigingen die mogelijk van invloed op uw gebruik van Configuration Manager.  

Deze informatie kan worden gewijzigd met toekomstige versies en kan elk afgeschafte functie, het product of het besturingssysteem niet bevatten.  

## <a name="how-to-use-this-information"></a>Het gebruik van deze informatie  
Wanneer een functie of het besturingssysteem eerst weergegeven wordt als verouderd, is ondersteuning voor het gebruik ervan met Configuration Manager gepland, worden verwijderd uit toekomstige versies van Configuration Manager. Deze informatie wordt verstrekt om te plannen voor alternatieven voor die functie of het besturingssysteem. Wanneer de eerste versie van Configuration Manager worden vrijgegeven in welke waarmee ondersteuning wordt verwijderd, wordt dit onderwerp is bijgewerkt om aan te geven die specifieke versie.  

Als ondersteuning voor een functie of het besturingssysteem wordt verwijderd, blijft het besturingssysteem of functie ondersteund wanneer u een eerdere versie van Configuration Manager, zolang deze versie van Configuration Manager ondersteuning. Echter, als u een versie van Configuration Manager, vrijgegeven nadat de datum of vermeld, die versie van Configuration Manager biedt geen ondersteuning.

Bijvoorbeeld, als een functie is gepland om de ondersteuning verwijderd met zou de eerste update uitgebracht na September 2016, ondersteuning voor die functie niet langer worden opgenomen in update 1610, dat in oktober van 2016 gepubliceerd.
-  Met Update 1610, zou u de functie niet meer ondersteund.
-  In dit onderwerp zou worden bijgewerkt om aan te geven ondersteuning met versie 1610 is verwijderd.
Echter, als u een eerdere versie die ondersteuning biedt voor de functie, zoals versie 1602 of 1606, blijft u kunt blijven gebruiken die functie pas de versie die u buiten-ondersteuning.

Zie voor meer informatie:
 - De [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle) website.
 - [Ondersteuning voor de huidige vertakking versies van Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).




## <a name="deprecated-operating-systems"></a>Afgeschaft besturingssystemen
### <a name="server-operating-systems"></a>Serverbesturingssystemen  

|**Besturingssystemen**|**Afschaffing eerst aangekondigd**|**Ondersteuning is verwijderd** |  
|-|-|-|  
|Windows Server 2008|10 juli 2015|Versie 1511 </br></br>Ondersteuning voor een sitesysteem is verwijderd. (Zie Opmerking 1).|  
|Windows Server 2008 R2|10 juli 2015| Versie 1702 (Zie Opmerking 2)|  

-   Opmerking 1: Dit besturingssysteem wordt niet ondersteund voor siteservers of sitesysteemrollen met uitzondering van het distributiepunt en het pull-distributiepunt. U kunt blijven gebruiken dit besturingssysteem als een distributiepunt tot buitengebruikstelling van deze ondersteuning is aangekondigd of dit besturingssysteem uitgebreide ondersteuning zijn verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

-   Opmerking 2:    Vanaf versie 1702, wordt dit besturingssysteem niet ondersteund voor siteservers of de meeste sitesysteemrollen, maar versies vóór 1702 blijven ondersteunen het gebruik ervan. Dit besturingssysteem ondersteunde is zichtbaar voor het statusmigratiepunt en distribueren sitesysteemrol (inclusief pull-distributiepunten, en voor PXE en multicast) tot buitengebruikstelling van deze ondersteuning is aangekondigd of dit besturingssysteem uitgebreide ondersteuningsperiode is verstreken. Vanaf versie 1602, u kunt een upgrade ter plekke het besturingssysteem van een site-server van Windows Server 2008 R2 en Windows Server 2012 R2.  

     Zie voor meer informatie over in-place upgrade uit van een besturingssysteem van de site-servers, de [In-place upgrade het besturingssysteem van siteservers met Windows Server 2008 R2](../../../core/plan-design/changes/whats-new-in-version-1602.md#bkmk_UpgradeOS) in sectie [wat gewijzigd in System Center Configuration Manager](../../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).



### <a name="client-operating-systems"></a>Client-besturingssystemen  

 Tenzij anders vermeld, wordt elk besturingssysteem dat wordt ondersteund als een Configuration Manager-client wordt ondersteund totdat de einddatum uitgebreide ondersteuning van dat besturingssysteem. Zie voor meer informatie over de uitgebreide ondersteuning einddatum de [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Als u voorafgaand aan de uitgebreide ondersteuning voor einddatum einde van ondersteuning voor Configuration Manager voor een besturingssysteem, worden een afschaffing datum en de datum van verwijdering ondersteuning voor dat besturingssysteem hier vermeld.  

|**Besturingssystemen**|**Afschaffing eerst aangekondigd**|**Ondersteuning is verwijderd**|  
|-|-|-|  
|Windows XP|10 juli 2015|Versie 1511|  
|Windows XP Embedded|10 juli 2015|Versie 1702|  
|Windows Server 2003|10 juli 2015|Versie 1511|  
|Windows Server 2003 R2|10 juli 2015|Versie 1511|  
|Windows Vista|10 juli 2015|Versie 1511|  
|Mac OS X 10,6 10,8|10 juli 2015|Versie 1511|  
|Windows Mobile 6.0 6.5|10 juli 2015|Versie 1511|  
|Nokia Symbian Belle|10 juli 2015|Versie 1511|  
|Windows CE 5.0 6.0|10 juli 2015|Versie 1511|  


## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Afgeschaft ondersteuning voor versies van SQL Server als een sitedatabase  

|**SQL Server-versies**|**Afschaffing eerst aangekondigd**|**Ondersteuning is verwijderd**|   
|-|-|-|  
|SQL Server 2008|10 juli 2015|Versie 1511|  
|SQL Server 2008 R2|10 juli 2015|Versie 1702|  

Als u moet de versie van SQL Server wilt bijwerken, raden wij de volgende methoden van eenvoudig complexe.
1. [SQL Server in-place upgrade](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (aanbevolen).
2. Een nieuwe versie van SQL Server op een nieuwe computer installeren en vervolgens [gebruikt u de optie datbase verplaatsen](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) van Configuration Manager setup uw siteserver verwijzen naar de nieuwe SQL Server.
3. Gebruik [back-up en herstel](/sccm/protect/understand/backup-and-recovery).


## <a name="deprecated-features"></a>Verouderde functies  

|**Functie**|**Afschaffing eerst aangekondigd**|**Ondersteuning is verwijderd**|  
|-|-|-|  
|Network Access Protection (NAP) - die in de System Center 2012 Configuration Manager|10 juli 2015|Versie 1511|  
|Buiten-Bandbeheer - die in de System Center 2012 Configuration Manager|16 oktober 2015|Versie 1511|
|Takenreeksen: <br /> -OSDPreserveDriveLetter  <br /><br /> Tijdens de implementatie van een besturingssysteem bepaalt standaard Windows Setup nu de beste stationsletter (meestal C:) gebruiken. Als u opgeven van een ander station moet worden gebruikt wilt, kunt u de locatie van de takenreeksstap besturingssysteem toepassen. Ga naar de **selecteert u de locatie waar u dit besturingssysteem toepassen** stellen, selecteer **logische stationsletter opgeven**, en kies het station dat u wilt gebruiken. |20 juni 2016 |Versie 1606 |
|Takenreeksen: <br /> -Schijf naar dynamische schijven converteren <br /> -Implementatiehulpprogramma's installeren |18 november 2016|Ondersteuning voor deze taak takenreeksen eindigt met de eerste update uitgebracht na 1 juni 2017.|
|Het Software Center is een nieuwe, moderne vormgeving. Apps die alleen in de Silverlight-afhankelijk zijn van het Application Catalog (gebruiker beschikbare apps) zou hebben gestaan nu weergegeven in Software Center op de **toepassingen** tabblad. De Application Catalog nog steeds toegankelijk zijn via de koppeling op de **installatiestatus** tabblad van het Software Center.<br><br>In de komende maanden wordt de vorige versie van het Software Center niet langer beschikbaar.<br><br>U kunt instellen om clients op het nieuwe Software Center gebruiken doordat de client-instelling, **Computeragent** > **nieuwe Software Center gebruiken**.<br><br>Zie voor meer informatie over Software Center [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/plan-design/plan-for-and-configure-application-management).|13 december 2016|Worden aangekondigd|
|Beheer van virtuele harde schijven (VHD's) met Configuration Manager. </br></br>Dit omvat het verwijderen van de opties voor een nieuwe VHD maken of beheren van een VHD met behulp van een takenreeks en het verwijderen van het knooppunt virtuele Hardeschijven van de Configuration Manager-console. </br></br>Wanneer deze ondersteuning wordt verwijderd, worden bestaande VHD's worden niet verwijderd, maar niet langer toegankelijk is vanuit de Configuration Manager-console.  |6 januari 2017 |Ondersteuning voor VHD's eindigt met de eerste update uitgebracht na 1 juni 2017.|
|System Center Configuration Manager Upgrade Assessment Tool. </br></br>Het hulpprogramma Upgradebeoordeling is afhankelijk van System Center Configuration Manager en Application Compatibility Toolkit (ACT) 6.x. De definitieve versie van ACT is in de Windows 10 v1511 ADK verzonden. Als er worden geen verdere updates van ACT, ondersteuning voor het hulpprogramma Upgradebeoordeling afgebroken. </br></br>Het hulpprogramma Upgradebeoordeling wordt vervangen door de [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) functie. Kennisgeving afschaffing is toegevoegd aan de [downloadpagina voor UAT](https://www.microsoft.com/download/details.aspx?id=37145) op 12-9-2016. |9/12/2016  | 11 juli 2017 |  


<br></br>
Aanvullende informatie voor functies verwijderd met versie 1511 van System Center Configuration Manager-versie:

###  <a name="bkmk_amt"></a>Buiten-Bandbeheer  
 Met Configuration Manager systeemeigen ondersteuning voor AMT-gebaseerde computers in de Configuration Manager-console is verwijderd.  

-   AMT-gebaseerde computers volledig beheerd blijven wanneer u de [Intel SCS-invoegtoepassing voor Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). De invoegtoepassing die u toegang biedt tot de nieuwste mogelijkheden voor het beheren van AMT, tijdens het verwijderen van beperkingen totdat Configuration Manager aanbrengen die wijzigingen kan is geïntroduceerd.  

-   Buiten-Bandbeheer in System Center 2012 Configuration Manager wordt niet beïnvloed door deze wijziging.  

###  <a name="bkmk_nap"></a>Network Access Protection  
 System Center Configuration Manager is ondersteuning voor Network Access Protection verwijderd. De functie in Windows Server 2012 R2 is gedeprecieerd en wordt verwijderd uit Windows 10.  

 Bekijk het gedeelte *Afgeschafte functionaliteit* van [Overzicht van Services voor netwerkbeleid en -toegang](https://technet.microsoft.com/library/hh831683.aspx) voor informatie over alternatieven voor netwerktoegangsbeveiliging.

