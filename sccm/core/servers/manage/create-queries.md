---
title: Query's maken
titleSuffix: Configuration Manager
description: Ontdek hoe u kunt maken en importeren van query's in System Center Configuration Manager. Bevat voorbeelden van query's en tips.
ms.custom: na
ms.date: 12/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: "5"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 32400ebcd834e3b98bf0f1ff6a1f6b41d8e12076
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>Query's maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt in dit onderwerp gebruiken bij het maken of importeren van query's in System Center Configuration Manager.  

##  <a name="BKMK_Create"></a> Query’s maken  
 Gebruik deze procedure kunt u query's maken in Configuration Manager.  

#### <a name="to-create-a-query"></a>Een query maken  

1.  Kies in de Configuration Manager-console **bewaking**.  

2.  In de **bewaking** werkruimte, kiest u **query's**. Klik op de **Start** tabblad, in de **maken** groep, kiest u **Query maken**.  

3.  Geef op het tabblad **Algemeen** van de **Wizard Query maken**een unieke naam en een optionele opmerking voor de query op.  

4.  Als u wilt importeren van een bestaande query Kies om verder te gebruiken als basis voor de nieuwe query **Query-instructie importeren**. In de **door Query Bladeren** dialoogvenster Selecteer een bestaande query die u wilt importeren, en kies vervolgens **OK**.  

5.  In de **objecttype** , selecteert u het type object die u wilt dat de query retourneert. In de volgende tabel staan enkele voorbeelden van het type object waar u naar kunt zoeken:  

    |Objecttype|Beschrijving|  
    |-----------------|-----------------|  
    |**Systeembron**|Gebruik dit om te zoeken naar typische systeemkenmerken, zoals de NetBIOS-naam van een apparaat, de clientversie, het IP-adres van de client en informatie van Active Directory Domain Services.|  
    |**Gebruikersbron**|Gebruiken om te zoeken naar gangbare gebruikersinformatie, zoals gebruikersnamen, namen van gebruikersgroepen en namen van beveiligingsgroepen.|  
    |**Implementatie**|Gebruiken om te zoeken naar gangbare kenmerken van een implementatie, zoals de implementatienaam, planning en de verzameling die is geïmplementeerd op.|  

6.  Kies **Query-instructie bewerken** openen de  *&lt;querynaam\>*  **instructie-eigenschappen** in het dialoogvenster.  

7.  Op de **algemene** tabblad de  *&lt;querynaam\>*  **instructie-eigenschappen** dialoogvenster geeft u de kenmerken die deze query retourneert en hoe ze worden weergegeven. Kies de **nieuw** pictogram van een nieuw kenmerk toe te voegen. U kunt ook **querytaal weergeven** invoeren of bewerken van de query rechtstreeks in WMI Query Language (WQL). Zie de sectie [Example WQL queries](#BKMK_Example) in dit onderwerp voor voorbeelden van WMI-query's.  

    > [!TIP]  
    > U kunt de volgende MSDN-naslagdocumentatie gebruiken bij het maken van uw eigen WQL-query's:  
    >   
    > -   [WQL (SQL voor WMI)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [WHERE-component](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [WQL-operators](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  Op de **Criteria** tabblad van de  *&lt;querynaam\>*  **instructie-eigenschappen** dialoogvenster geeft u de criteria die worden gebruikt om de resultaten van de query te verfijnen. U kunt bijvoorbeeld alleen bronnen retourneren met een sitecode van **XYZ** in de queryresultaten. U kunt meerdere criteria voor een query configureren.  

    > [!IMPORTANT]  
    > Als u een query zonder criteria maakt, retourneert de query alle apparaten in de verzameling **Alle systemen** .  

9. Op de **Joins** tabblad de  *&lt;querynaam\>*  **instructie-eigenschappen** in het dialoogvenster kunt u gegevens uit twee verschillende kenmerken combineren in uw queryresultaten. Hoewel de Configuration Manager automatisch query's samenvoegt wanneer u verschillende kenmerken voor het queryresultaat kiest de **Joins** tabblad biedt meer geavanceerde opties. De kenmerkklassen die ondersteuning biedt voor System Center 2012 Configuration Manager worden weergegeven in de volgende tabel:  

    |Type samenvoeging|Beschrijving|  
    |---------------|-----------------|  
    |Binnen|Geeft alleen overeenkomende resultaten — altijd gebruikt door samenvoegingen die automatisch worden gemaakt.|  
    |Links|Geeft alle resultaten voor het basiskenmerk weer en alleen de overeenkomende resultaten voor het samenvoegingskenmerk.|  
    |Rechts|Geeft alle resultaten voor het samenvoegingskenmerk weer en alleen de overeenkomende resultaten voor het basiskenmerk.|  
    |Volledig|Geeft alle resultaten weer voor zowel het basiskenmerk als het samenvoegingskenmerk.|  

     Raadpleeg de SQL Server-documentatie voor meer informatie over het gebruik van samenvoegingsbewerkingen.  

10. Kies **OK** sluiten de  *&lt;querynaam\>*  **instructie-eigenschappen** in het dialoogvenster.  

11. Op de **algemene** tabblad van de **Wizard Query maken**, opgeven of de resultaten van deze query niet beperkt tot de leden van een verzameling of ze zijn beperkt tot de leden van een opgegeven verzameling, of er is een prompt voor een verzameling telkens wanneer de query wordt uitgevoerd.  

12. Voltooi de wizard om de query te maken. De nieuwe query wordt weergegeven in het knooppunt **Query's** in de werkruimte **Bewaking** .  

##  <a name="BKMK_Import"></a> Query’s importeren  
 Gebruik deze procedure kunt u een query importeren in Configuration Manager. Zie voor meer informatie over het exporteren van query's [query's in System Center Configuration Manager beheren](../../../core/servers/manage/manage-queries.md).  

#### <a name="to-import-a-query"></a>Een query importeren  

1.  Kies in de Configuration Manager-console **bewaking**.  

2.  In de **bewaking** werkruimte, kiest u **query's**. Op de **Start** tabblad, in de **maken** groep, kiest u **objecten importeren**.  

3.  Op de **MOF-bestandsnaam** pagina van de **Wizard objecten importeren**, kies **Bladeren** selecteert het Managed Object Format (MOF) bestand met de query die u wilt importeren.  

4.  Controleer de informatie die over de te importeren query wordt weergegeven en voltooi de wizard. De nieuwe query wordt weergegeven op de **query's** knooppunt in de **bewaking** werkruimte.  

##  <a name="BKMK_Example"></a> Example WQL queries

In deze sectie vindt u voorbeelden van WMI-query's die u kunt gebruiken in uw hiërarchie of die u voor andere doeleinden kunt wijzigen. Deze query's, kiest u **querytaal weergeven** in de **eigenschappen Query-instructie** in het dialoogvenster. Kopieer en plak de query in vervolgens de **Query-instructie** veld.  

> [!TIP]  
> Het jokerteken gebruiken `%` om willekeurige tekenreeks aan te geven. Bijvoorbeeld, `%Visio%` retourneert Microsoft Office Visio 2010.  

### <a name="computers-that-run-windows-7"></a>Computers met Windows 7

Gebruik de volgende query om de NetBIOS-naam en besturingssysteemversie te retourneren van alle computers met Windows 7.  

> [!TIP]  
> Wijzigen voor computers waarop Windows Server 2008 R2 wordt uitgevoerd, `%Workstation 6.1%` naar `%Server 6.1%`.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>Computers met een specifiek softwarepakket geïnstalleerd  

Gebruik de volgende query om de NetBIOS-naam en softwarepakketnaam te retourneren van alle computers waarop een specifiek softwarepakket is geïnstalleerd. In dit voorbeeld worden alle computers weergegeven waarop een versie van Microsoft Visio is geïnstalleerd. Vervang `%Visio%` met het softwarepakket dat u wilt zoeken.  

> [!TIP]  
> Deze query zoekt naar het softwarepakket op basis van de namen die worden weergegeven in de lijst met programma's in het Configuratiescherm.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit"></a>Computers die zich in een specifieke organisatie-eenheid van Active Directory Domain Services

Gebruik de volgende query te retourneren van de NetBIOS-naam en de naam van de organisatie-eenheid (OE) van alle computers in een opgegeven organisatie-eenheid. Vervang de tekst `OU Name` met de naam van de organisatie-eenheid die u wilt zoeken.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>Computers met een specifieke NetBIOS-naam

Gebruik de volgende query om de NetBIOS-naam te retourneren van alle computers die met een specifieke tekenreeks beginnen. In dit voorbeeld retourneert de query alle computers met een NetBIOS-naam die met begint `ABC`.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> Apparaten van een bepaald type

Apparaattypen worden opgeslagen in de Configuration Manager-database onder de bronklasse **sms_r_system** en de naam van het kenmerk **AgentEdition**. Gebruik de volgende query om op te halen, alleen de apparaten die overeenkomen met de agenteditie van het apparaattype dat u opgeeft:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>  
```  

Gebruik een van de volgende waarden voor  *&lt;apparaat-ID\>*:  

|Apparaattype|Waarde van AgentEdition|  
|-----------------|---------------------------|  
|Windows desktop- of -computer|0|  
|Windows ARM-apparaat (waarop Windows RT wordt uitgevoerd)|1|  
|Windows Mobile 6.5|2|  
|Nokia Symbian|3|  
|Windows Phone|4|  
|Mac-computer|5|  
|Windows CE|6|  
|Windows Embedded|7|  
|iOS|8|  
|iPad|9|  
|iPod Touch|10|  
|Android|11|  
|Intel System-on-a-Chip|12|  
|UNIX- en Linux-servers|13|  
|Apple Mac OS (MDM)|14|
|Microsoft HoloLens (MDM)|15|
|De Microsoft Surface Hub (MDM)|16|
|Android for Work|17|

 Een voorbeeld: als u wilt dat de query alleen Mac-computers retourneert, gebruikt u de volgende query:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>Zie tevens  
 [Bewerkingen en onderhoud voor query's in System Center Configuration Manager](../../../core/servers/manage/operations-and-maintenance-for-queries.md)
