---
title: Query&quot;s maken | Microsoft-documenten
description: Ontdek hoe u kunt maken en query&quot;s in System Center Configuration Manager te importeren. Voorbeeld van de query&quot;s en tips bevat.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 89bd798339489071fdb69325c957fefda32621e9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>Het maken van query's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende secties in dit onderwerp voor hulp bij het maken of importeren van query's in System Center Configuration Manager.  

-   [How to Create Queries](#BKMK_Create)  

-   [How to Import Queries](#BKMK_Import)  

-   [Example WQL Queries](#BKMK_Example)  

##  <a name="BKMK_Create"></a> Query’s maken  
 Gebruik deze procedure voor het maken van query's in Configuration Manager.  

#### <a name="to-create-a-query"></a>Een query maken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Klik in de werkruimte **Bewaking** op **Query's** en klik vervolgens op het tabblad **Start** in de groep **Maken** op **Query maken**.  

3.  Geef op het tabblad **Algemeen** van de **Wizard Query maken**een unieke naam en een optionele opmerking voor de query op.  

4.  Als u een bestaande query wilt importeren en als basis voor de nieuwe query wilt gebruiken, klikt u op **Query-instructie importeren** en selecteert u in het dialoogvenster **Door query bladeren** een bestaande query die u wilt importeren en klikt u vervolgens op **OK**.  

5.  Selecteer in de lijst **Objecttype** het type object dat u wilt dat de query retourneert. In de volgende tabel staan enkele voorbeelden van het type object waar u naar kunt zoeken:  

    |Objecttype|Beschrijving|  
    |-----------------|-----------------|  
    |**Systeembron**|Gebruik dit om te zoeken naar typische systeemkenmerken, zoals de NetBIOS-naam van een apparaat, de clientversie, het IP-adres van de client en informatie van Active Directory Domain Services.|  
    |**Gebruikersbron**|Gebruik dit om te zoeken naar gangbare gebruikersinformatie, zoals gebruikersnamen, namen van gebruikersgroepen en namen van beveiligingsgroepen.|  
    |**Implementatie**|Gebruik dit om te zoeken naar gangbare kenmerken van een implementatie, zoals de implementatienaam, planning, en de verzameling waarin deze is geïmplementeerd.|  

6.  Klik op **Query-instructie bewerken** openen van de  *&lt;querynaam\>***instructie eigenschappen** in het dialoogvenster.  

7.  Op de **algemeen** tabblad de  *&lt;querynaam\>***instructie eigenschappen** dialoogvenster Geef de kenmerken die door deze query retourneert en hoe ze worden weergegeven. Klik op het pictogram **Nieuw** om een nieuw kenmerk toe te voegen. U kunt ook op **Querytaal weergeven** klikken om de query te openen of deze rechtstreeks in WMI Query Language (WQL) te bewerken. Zie de sectie [Example WQL queries](#BKMK_Example) in dit onderwerp voor voorbeelden van WMI-query's.  

    > [!TIP]  
    >  U kunt de volgende MSDN-naslagdocumentatie gebruiken bij het maken van uw eigen WQL-query's:  
    >   
    >  -   [WQL (SQL voor WMI)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [WHERE-component](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [WQL-operators](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  Op de **Criteria** tabblad van het  *&lt;querynaam\>***instructie eigenschappen** dialoogvenster geeft u de criteria die worden gebruikt om de resultaten van de query te verfijnen. U kunt bijvoorbeeld alleen bronnen retourneren met een sitecode van **XYZ** in de queryresultaten. U kunt meerdere criteria voor een query configureren.  

    > [!IMPORTANT]  
    >  Als u een query zonder criteria maakt, retourneert de query alle apparaten in de verzameling **Alle systemen** .  

9. Op de **lid** tabblad de  *&lt;querynaam\>***instructie eigenschappen** in het dialoogvenster kunt u gegevens uit twee verschillende kenmerken combineren in uw queryresultaten. Hoewel query joins Configuration Manager automatisch gemaakt wanneer u verschillende kenmerken voor het queryresultaat kiest de **Joins** tabblad biedt meer geavanceerde opties. Het kenmerkklassen ondersteund door System Center 2012 Configuration Manager worden weergegeven in de volgende tabel:  

    |Type samenvoeging|Beschrijving|  
    |---------------|-----------------|  
    |Binnen|Hiermee wordt alleen overeenkomende resultaten - altijd gebruikt door joins die automatisch worden gemaakt.|  
    |Links|Geeft alle resultaten voor het basiskenmerk weer en alleen de overeenkomende resultaten voor het samenvoegingskenmerk.|  
    |Rechts|Geeft alle resultaten voor het samenvoegingskenmerk weer en alleen de overeenkomende resultaten voor het basiskenmerk.|  
    |Volledig|Geeft alle resultaten weer voor zowel het basiskenmerk als het samenvoegingskenmerk.|  

     Zie de documentatie van uw SQL Server voor meer informatie over het gebruik van samenvoegingsbewerkingen.  

10. Klik op **OK** sluit de  *&lt;querynaam\>***instructie eigenschappen** in het dialoogvenster.  

11. Geef op het tabblad **Algemeen** van de **Wizard Query maken**op of de resultaten van deze query niet beperkt zijn tot de leden van een verzameling, beperkt zijn tot de leden van een opgegeven verzameling of elke keer naar een verzameling vragen wanneer de query wordt uitgevoerd.  

12. Voltooi de wizard om de query te maken. De nieuwe query wordt weergegeven in het knooppunt **Query's** in de werkruimte **Bewaking** .  

##  <a name="BKMK_Import"></a> Query’s importeren  
 Gebruik deze procedure als u een query importeert in Configuration Manager. Zie voor meer informatie over het exporteren van query's [query's in System Center Configuration Manager beheren](../../../core/servers/manage/manage-queries.md).  

#### <a name="to-import-a-query"></a>Een query importeren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Klik in de werkruimte **Bewaking** op **Query's** en klik vervolgens op het tabblad **Start** in de groep **Maken** op **Objecten importeren**.  

3.  Klik op de pagina **MOF-bestandsnaam** van de **Wizard Objecten importeren**op **Bladeren** om het MOF-bestand (Managed Object Format) te selecteren met de query die u wilt importeren.  

4.  Controleer de informatie die over de te importeren query wordt weergegeven en voltooi de wizard. De nieuwe query wordt weergegeven in het knooppunt **Query's** in de werkruimte **Bewaking** .  

##  <a name="BKMK_Example"></a> Example WQL queries  
 In deze sectie vindt u voorbeelden van WMI-query's die u kunt gebruiken in uw hiërarchie of die u voor andere doeleinden kunt wijzigen. Als u query's wilt gebruiken, klikt u op **Querytaal weergeven** in het dialoogvenster **Eigenschappen query-instructie** en kopieert en plakt u de query in het veld **Query-instructie** .  

> [!TIP]  
>  Gebruik het jokerteken **%** om willekeurige tekenreeks aan te geven. Een voorbeeld: **%Visio%** retourneert Microsoft Office Visio 2010.  

### <a name="computers-that-run-windows-7"></a>Computers met Windows 7  
 Gebruik de volgende query om de NetBIOS-naam en besturingssysteemversie te retourneren van alle computers met Windows 7.  

> [!TIP]  
>  Om computers te retourneren waarop Windows Server 2008 R2 wordt uitgevoerd, wijzigt u **%Workstation 6.1%** in **%Server 6.1%**.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>Computers met een specifiek softwarepakket geïnstalleerd  
 Gebruik de volgende query om de NetBIOS-naam en softwarepakketnaam te retourneren van alle computers waarop een specifiek softwarepakket is geïnstalleerd. In dit voorbeeld worden alle computers weergegeven waarop een versie van Microsoft Visio is geïnstalleerd. Vervang **%Visio%** door het softwarepakket dat u wilt zoeken.  

> [!TIP]  
>  Deze query zoekt naar het softwarepakket op basis van de namen die worden weergegeven in de lijst met programma's in het Configuratiescherm.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit-ou"></a>Computers die zich in een specifieke Active Directory Domain Services-organisatie-eenheid bevinden  
 Gebruik de volgende query om de NetBIOS-naam en de naam van de organisatie-eenheid van alle computers in een opgegeven organisatie-eenheid te retourneren. Vervang de tekst **OU Name** door de naam van de organisatie-eenheid die u wilt zoeken.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>Computers met een specifieke NetBIOS-naam  
 Gebruik de volgende query om de NetBIOS-naam te retourneren van alle computers die met een specifieke tekenreeks beginnen. In dit voorbeeld retourneert de query alle computers met een NetBIOS-naam die begint met **ABC**.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> Apparaten van een bepaald type  
 Apparaattypen worden opgeslagen in de Configuration Manager-database onder de bronklasse **sms_r_system** en de naam van het kenmerk **AgentEdition**. Gebruik de volgende query om alleen de apparaten op te halen die overeenkomen met de agenteditie van het apparaattype dat u opgeeft:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>  
```  

 Gebruik een van de volgende waarden voor  *&lt;apparaat-ID\>*:  

|Apparaattype|Waarde van AgentEdition|  
|-----------------|---------------------------|  
|Windows-desktopcomputer of Windows-laptopcomputer|0|  
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
|Intel System On a Chip|12|  
|UNIX- en Linux-servers|13|  

 Een voorbeeld: als u wilt dat de query alleen Mac-computers retourneert, gebruikt u de volgende query:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>Zie ook  
 [Bewerkingen en onderhoud voor query's in System Center Configuration Manager](../../../core/servers/manage/operations-and-maintenance-for-queries.md)

