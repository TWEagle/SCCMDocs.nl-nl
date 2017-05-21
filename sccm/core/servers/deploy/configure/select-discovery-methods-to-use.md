---
title: Selecteer detectiemethoden voor Configuration Manager | Microsoft-documenten
description: Bekijk de overwegingen voor welke methoden te gebruiken en op welke sites om ze uit te voeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f72317cefab5ce8cad13b3120c3c93c856fa40b7
ms.openlocfilehash: 4b6be888be2ad6c1f5e7c0be33d9830bb870114e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="select-discovery-methods-to-use-for-system-center-configuration-manager"></a>Detectiemethoden selecteren om te gebruiken voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het correct en doeltreffend gebruik van detectie voor System Center Configuration Manager, moet u rekening houden met welke methoden te gebruiken en op welke sites om ze uit te voeren.  

 Omdat detectie grote volumes netwerkverkeer genereren kan en de resulterende detectiegegevensrecords (DDR's) veel CPU-bronnen tijdens de verwerking gebruiken kunnen, gebruikt u alleen die detectiemethoden die u nodig hebt om uw doelstellingen te behalen. U kunt starten met slechts één of twee detectiemethoden en daarna de bijkomende methoden op een gecontroleerde manier uit te breiden de mate van detectie in uw omgeving later inschakelt. De informatie in dit onderwerp kunt u geïnformeerde beslissingen te nemen.  

 Zie voor meer informatie over de verschillende detectiemethodes [over detectiemethoden voor System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  

## <a name="select-methods-to-discover-different-things"></a>Methoden voor het detecteren van andere dingen selecteren  
 Om te mogelijke Configuration Manager-clientcomputers of Gebruikersbronnen detecteren, moet u de geschikte detectiemethoden inschakelen. U kunt verschillende combinaties van detectiemethoden gebruiken om verschillende bronnen te vinden en aanvullende informatie over die bronnen detecteren. De detectiemethoden waarmee u bepaalt het type resources die zijn gedetecteerd en de Configuration Manager-services en -agents worden gebruikt in het detectieproces. Ze bepalen ook het soort informatie over bronnen die u kunt detecteren.  

### <a name="discover-computers"></a>Computers detecteren   
Wanneer u computers detecteren wilt, kunt u **Active Directory-Systeemdetectie** of **netwerkdetectie**.  

 Bijvoorbeeld, als u detecteren van bronnen die de Configuration Manager-client installeren wilt kunnen voordat u clientpushinstallatie gebruikt, misschien voert u Active Directory System Discovery. Met deze optie kunt u niet alleen de bron, maar ook basisinformatie zelfs uitgebreide informatie erover uit Active Directory Domain Services detecteren. Deze informatie kan nuttig zijn in opbouwen van complexe query's en verzamelingen om te gebruiken voor de toewijzing van clientinstellingen of inhoudimplementatie.

U kan ook netwerkdetectie uitvoeren en de opties ervan gebruiken voor het detecteren van het besturingssysteem van bronnen (vereist om later te gebruiken clientpushinstallatie). Netwerkdetectie vindt u informatie over uw netwerktopologie die u niet kunt verwerven met andere detectiemethoden. Deze methode niet zo is, biedt maar u geen informatie over uw Active Directory-omgeving.

 Er is ook een methode aangeroepen **Heartbeat-detectie**. Het is mogelijk alleen Heartbeat-detectie gebruiken om de detectie van clients die u met andere methoden dan clientpushinstallatie installeerde te forceren. Echter, in tegenstelling tot andere detectiemethoden kan Heartbeat-detectie geen computers detecteren die een actieve Configuration Manager-client niet is. Dit retourneert een beperkt aantal informatie bedoeld om een bestaand databaserecord te behouden in plaats van de basis van dat record. Informatie die door Heartbeat-detectie wordt verzonden mogelijk onvoldoende voor het opbouwen van complexe query's of verzamelingen.  

 Als u **Active Directory Group Discovery** voor het detecteren van het lidmaatschap van een bepaalde groep, kunt u beperkte systeem- of informatie detecteren. Dit is geen vervanging voor een volledige detectie van computers, maar u kunt algemene informatie opgeven. Deze informatie is onvoldoende voor clientpushinstallatie.  

### <a name="discover-users"></a>Detecteren van gebruikers   
Wanneer u informatie detecteren over gebruikers wilt, gebruik **Active Directory User Discovery**. Net als bij Active Directory-Systeemdetectie, detecteert deze methode of gebruikers van Active Directory. Het bevat algemene informatie, naast uitgebreide Active Directory-informatie. U kunt deze informatie gebruiken om complexe query's en verzamelingen vergelijkbaar met die voor computers te bouwen.  

### <a name="discover-group-information"></a>Groepsinformatie detecteren   
Wanneer u informatie detecteren over groepen en groepslidmaatschappen wilt, gebruiken **Active Directory Group Discovery**. Deze detectiemethode maakt bronrecords voor beveiligingsgroepen.  

 Deze methode kunt u zoeken naar een specifieke Active Directory-groep om de leden van die groep, en eventueel geneste groepen binnen die groep te identificeren. U kunt deze methode ook gebruiken om te zoeken naar een Active Directory-locatie voor groepen en recursief zoeken naar elke onderliggende container van die locatie in Active Directory Domain Services.  

 Deze detectiemethode kan ook zoeken naar het lidmaatschap van distributiegroepen. Dit kan de groepsrelaties van zowel gebruikers als computers identificeren.  

 Als u een groep detecteert, kunt u beperkte informatie over de leden ervan detecteren. Dit vervangt de Active Directory systeem of de gebruiker detectiemethoden, maar. Het is doorgaans onvoldoende om te maken van complexe query's en verzamelingen of dienen als basis van een push-clientinstallatie.  

### <a name="discover-infrastructure"></a>Infrastructuur detecteren   
Er zijn twee methoden voor het detecteren van netwerkinfrastructuur, kunt u **Active Directory-Forestdetectie** en **netwerkdetectie**.  

 Detectie van Active Directory-Forest gebruiken om te zoeken naar een Active Directory-forest voor informatie over subnetten en Active Directory-siteconfiguraties. Deze configuraties kunnen vervolgens automatisch worden ingevoerd in Configuration Manager als grenslocaties.  

 Als u detecteren van uw netwerktopologie wilt, kunt u netwerkdetectie gebruikt. Hoewel andere detectiemethoden informatie geven over naar Active Directory Domain Services, en de huidige netwerklocatie van een client kan identificeren, geven ze geen infrastructuur informatie op basis van de subnets en de routertopologie van uw netwerk.  

##  <a name="bkmk_shared"></a>Detectiegegevens gedeeld tussen sites  
 Nadat Configuration Manager detetctietgegevens heeft toegegvoegd aan een database, worden ze vlug gedeeld tussen alle sites in de hiërarchie. Omdat er meestal geen voordeel gehaald wordt uit het detecteren van dezelfde informatie op verschillende sites in uw hiërarchie, kunt u slechts één exemplaar van elke detectiemethode die u gebruikt om uit te voeren op een enkele site. Er is een goed idee om dit te doen in plaats van meerdere instanties van één enkele methode op verschillende sites.  

 Voor bepaalde omgevingen kan deze zich echter nuttig zijn om toe te wijzen dezelfde detectiemethode om uit te voeren op verschillende sites, elk met een afzonderlijke configuratie en planning. Wanneer u netwerkdetectie gebruikt, wilt u mogelijk geeft elke site voor het detecteren van het lokale netwerk, in plaats van probeert netwerklocaties te detecteren alle via een WAN.

Als u meerdere exemplaren van de dezelfde detectiemethoden om uit te voeren op verschillende sites configureert, van de configuratie van elke site zorgvuldig plannen. U wilt voorkomen dat twee of meer sites detecteren dezelfde bronnen van uw netwerk of een Active Directory. Dit kan aanzienlijk meer netwerkbandbreedte gebruiken en dubbele DDR's creëren.

De volgende tabel identificeert op welke sites u de verschillende detectiemethodes kunt instellen.  

|Detectiemethode|Ondersteunde locaties|  
|----------------------|-------------------------|  
|Detectie van Active Directory-forests|Centrale beheersite<br /><br /> Primaire site|  
|Active Directory-groepdetectie|Primaire site|  
|Active Directory-systeemdetectie|Primaire site|  
|Detectie Active Directory-gebruiker|Primaire site|  
|Heartbeat-detectie<sup>1</sup>|Primaire site|  
|Netwerkdetectie|Primaire site<br /><br /> Secundaire site|  

 <sup>1</sup> secundaire sites kunnen geen Heartbeat-detectie configureren, maar kunnen de Heartbeat-DDR van een client ontvangen.  

 Wanneer secundaire sites netwerkdetectie uitvoeren of Heartbeat-detectie DDR's ontvangen, dragen ze de DDR door replicatie op basis van bestanden naar hun bovenliggende primaire site. Dit komt doordat er alleen primaire sites en centrale beheersites DDR's kunnen verwerken. Zie voor meer informatie over hoe DDR's verwerkt [over gegevensrecords van detectie](../../../../core/servers/deploy/configure/run-discovery.md#BKMK_DDRs).  

## <a name="considerations-for-different-discovery-methods"></a>Overwegingen voor de verschillende detectiemethodes  
 Omdat elke site server- en andere, is het een goed idee om uw eerste configuraties voor de detectie te beperken. Vervolgens nauw bewaak elke site tot zijn vermogen om de detectiegegevens die wordt gegenereerd te verwerken.  

Bij het gebruik van een **Active Directory** detectiemethode voor systemen, gebruikers of groepen:  

-   Voer detectie uit op een site die een snelle netwerkverbinding naar uw domeincontrollers heeft.  

-   Overweeg de Active Directory-replicatietopologie om ervoor te zorgen detectie toegang heeft tot de meest recente informatie.  

-   Overweeg het bereik van de detectieconfiguratie en beperk detectie tot enkel deze Active Directory-locaties en groepen die u dient te detecteren.  

Als u **netwerkdetectie**:  

-   Gebruik een beperkte initiële configuratie om uw netwerktopologie te identificeren.  

-   Nadat u uw netwerktopografie hebt geïdentificeerd, instellen netwerkdetectie uitgevoerd op specifieke sites die zijn centrale tot de netwerkgebieden die u meer volledig wilt detecteren.  

Omdat **Heartbeat-detectie** kan niet worden uitgevoerd op een specifieke site, u moet geen in rekening brengen in de algemene planning van de locaties waar detectie moet worden uitgevoerd.  

##  <a name="bkmk_best"></a>Aanbevolen procedures voor detectie  
Voor de beste resultaten bij de detectie raden we het volgende:

 - **Voer Active Directory-Systeemdetectie en Active Directory User Discovery vóór u detectie van Active Directory-groepen.**  

 Wanneer detectie van Active Directory-groepen een eerder gedetecteerde gebruiker of computer als een lid van een groep, probeert ze de basisdetails voor de gebruiker of computer te detecteren. Omdat detectie voor Active Directory-groepen niet geoptimaliseerd is voor dit type detectie, kan dit proces langzaam veroorzaken. Daarnaast identificeert detectie voor Active Directory-groepen enkel de Basisdetails over gebruikers en computers detecteert, en maakt niet een volledige gebruiker of computer detectierecord. Wanneer u Active Directory-Systeemdetectie en Active Directory-Gebruikersdetectie uitvoert, zijn de bijkomende Active Directory-attributen voor elk objecttype beschikbaar. Als gevolg hiervan Active Directory-Systeemdetectie efficiënter uitgevoerd.  

- **Bij het instellen van Active Directory Group Discovery, geef dan enkel groepen die u met Configuration Manager gebruikt.**  

 Het gebruik van bronnen door detectie voor Active Directory-groepen, opgeven om te bepalen alleen de groepen die u gebruikt met Configuration Manager. Dit komt doordat de detectie van Active Directory-groepen recursief elke groep doorzoekt die deze voor gebruikers, computers en geneste groepen detecteert. Het doorzoeken van elke geneste groep kan het bereik van detectie van Active Directory-groepen uitbreiden en de prestaties doen verminderen. Daarnaast bij het instellen van detectie van verschillen voor Active Directory Group Discovery, controleert de detectiemethode elke groep op wijziging. Dit vermindert verder de prestaties wanneer de methode onnodige groepen moet doorzoeken.  

- **Instellen van detectiemethoden gebruiken met een langer interval tussen volledige detecties, en een frequentere periode voor detectie van verschillen.**  

 Omdat detectie van verschillen minder bronnen dan een volledige detectiecyclus gebruikt, en nieuwe of gewijzigde bronnen in Active Directory kan identificeren, kunt u Verminder de frequentie van volledige detectiecycli wekelijks (of minder). Detectie van verschillen voor Active Directory-Systeemdetectie, Active Directory-Gebruikersdetectie en detectie van Active Directory-groepen identificeert bijna alle de wijzigingen van Active Directory-objecten en kan nauwkeurige detectiegegevens voor bronnen behouden.  

- **Active Directory-detectiemethoden worden uitgevoerd op een primaire site die een netwerklocatie die het dichtst bij uw Active Directory-domeincontroller heeft.**  

 Ter verbetering van de prestaties van Active Directory-detectie het een goed idee om uit te voeren detecteren op een primaire site heeft die een snelle netwerkverbinding naar uw domeincontrollers. Als u dezelfde Active Directory-detectiemetjode op meerdere sites uitvoert, stelt u elke detectiemethode om overlapping te voorkomen. In tegenstelling tot eerdere versies van Configuration Manager detectiegegevens gedeeld tussen sites. Daarom is het niet nodig voor het detecteren van dezelfde informatie op meerdere sites. Zie voor meer informatie [detectiegegevens worden gedeeld tussen sites](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md#bkmk_shared).  

- **Detectie van Active Directory-Forest worden uitgevoerd op slechts één site wanneer u plan bent om automatisch grenzen te maken van de detectiegegevens.**  

 Als u Active Directory-Forestdetectie op meer dan één site in een hiërarchie uitvoert, is het een goed idee om in te schakelen alleen opties voor het automatisch grenzen te maken op een enkele site. Dit komt doordat wanneer Active Directory-Forestdetectie op elke site uitvoert en ze grenzen maakt, Configuration Manager deze grenzen niet in één enkel grensobject samenvoegen. Wanneer u detectie van Active Directory-Forest automatisch om grenzen te maken op meerdere sites configureert, kan het resultaat zijn dubbele grensobjecten zijn in de Configuration Manager-console.  

