---
title: Detectiemethoden selecteren
titleSuffix: Configuration Manager
description: Bekijk de overwegingen voor welke methoden te gebruiken en op welke sites uitvoeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: "9"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b932c4670521af366c5cb40adf5b1076263a9c8e
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="select-discovery-methods-to-use-for-system-center-configuration-manager"></a>Detectiemethoden selecteren om te gebruiken voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het correct en doeltreffend gebruik van detectie voor System Center Configuration Manager, moet u rekening houden met welke methoden te gebruiken en op welke sites uitvoeren.  

 Omdat detectie een grote hoeveelheid netwerkverkeer genereren kan en de resulterende detectiegegevensrecords (DDR's) veel CPU-bronnen tijdens de verwerking gebruiken kunnen, gebruikt u alleen die detectiemethoden die u nodig hebt om uw doelstellingen te behalen. U mogelijk starten met slechts één of twee detectiemethoden en later extra methoden inschakelen op een gecontroleerde manier voor het uitbreiden van het niveau van detectie in uw omgeving. De informatie in dit onderwerp kunt u gefundeerde beslissingen te nemen.  

 Zie voor meer informatie over de verschillende detectiemethoden [over detectiemethoden voor System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  

## <a name="select-methods-to-discover-different-things"></a>Methoden voor het detecteren van verschillende dingen selecteren  
 Voor het detecteren van mogelijke Configuration Manager-clientcomputers of Gebruikersbronnen, moet u de geschikte detectiemethoden inschakelen. U kunt verschillende combinaties van detectiemethoden gebruiken om verschillende bronnen te vinden en aanvullende informatie over die bronnen detecteren. De detectiemethoden die u gebruikt, bepalen het type bronnen die zijn gedetecteerd en welke Configuration Manager-services en agents worden gebruikt in het detectieproces. Ze bepalen ook het type informatie over bronnen die u kunt detecteren.  

### <a name="discover-computers"></a>Computers detecteren   
Als u computers detecteren wilt, kunt u **Active Directory-Systeemdetectie** of **netwerkdetectie**.  

 Als u detecteren van bronnen die Configuration Manager-client installeren wilt kunnen voordat u clientpushinstallatie gebruikt, kunt u bijvoorbeeld Active Directory-Systeemdetectie uitvoeren. Met deze optie kunt u niet alleen detecteren van de bron, maar ook basisinformatie zelfs uitgebreide informatie over het uit Active Directory Domain Services te detecteren. Deze informatie kan nuttig zijn bij het bouwen van complexe query's en verzamelingen om te gebruiken voor de toewijzing van clientinstellingen of inhoudimplementatie zijn.

U kan ook netwerkdetectie uitvoeren en de opties ervan gebruiken voor het detecteren van het besturingssysteem van bronnen (vereist voor de push-clientinstallatie later gebruiken). Netwerkdetectie vindt u informatie over uw netwerktopologie die u niet kunt verwerven met andere detectiemethoden. Deze methode niet zo is, biedt maar u geen informatie over uw Active Directory-omgeving.

 Er is ook een aangeroepen methode **Heartbeat-detectie**. Het is mogelijk alleen Heartbeat-detectie gebruiken om de detectie van clients die u met andere methoden dan clientpushinstallatie installeerde te forceren. Echter, in tegenstelling tot andere detectiemethoden kan Heartbeat-detectie geen computers detecteren die geen een actieve Configuration Manager-client. Deze retourneert een beperkte set van informatie, bedoeld om een bestaand databaserecord te behouden in plaats van op basis van deze record. Informatie verzonden door Heartbeat-detectie is mogelijk niet voldoende zijn voor het bouwen van complexe query's en verzamelingen.  

 Als u **Active Directory Group Discovery** voor het detecteren van het lidmaatschap van een bepaalde groep, kunt u beperkte systeem- of informatie detecteren. Dit is geen vervanging voor een volledige detectie van computers, maar u kunt algemene informatie opgeven. Deze informatie is onvoldoende voor clientpushinstallatie.  

### <a name="discover-users"></a>Detecteren van gebruikers   
Als u detecteren van informatie over gebruikers wilt, gebruik **Active Directory-Gebruikersdetectie**. Net als bij Active Directory-Systeemdetectie, deze methode detecteert gebruikers uit Active Directory. Het bevat basisinformatie, naast uitgebreide Active Directory-informatie. U kunt deze informatie gebruiken om complexe query's en verzamelingen die overeenkomen met die voor computers te maken.  

### <a name="discover-group-information"></a>Groepsinformatie detecteren   
Als u detecteren van informatie over groepen en groepslidmaatschappen wilt, gebruik **Active Directory Group Discovery**. Deze detectiemethode maakt bronrecords voor beveiligingsgroepen.  

 U kunt deze methode gebruiken om te zoeken van een specifieke Active Directory-groep voor het identificeren van de leden van die groep, en eventueel geneste groepen binnen die groep. U kunt deze methode ook gebruiken om te zoeken van een Active Directory-locatie voor groepen en recursief zoeken naar elke onderliggende container van die locatie in Active Directory Domain Services.  

 Deze detectiemethode kan ook zoeken in het lidmaatschap van distributiegroepen. Dit kan de groepsrelaties van zowel gebruikers als computers identificeren.  

 Wanneer u een groep detecteert, kunt u ook beperkte informatie over de leden ervan detecteren. Dit is de Active Directory-systeem of gebruiker detectiemethoden, echter geen vervanging. Het is doorgaans onvoldoende is om te fungeren als de basis van een push-clientinstallatie of bouwen van complexe query's en verzamelingen.  

### <a name="discover-infrastructure"></a>Infrastructuur detecteren   
Er zijn twee methoden die u gebruiken kunt voor het detecteren van netwerkinfrastructuur, **Active Directory-Forestdetectie** en **netwerkdetectie**.  

 Detectie van Active Directory-Forest gebruiken om te zoeken van een Active Directory-forest voor informatie over subnetten en Active Directory-siteconfiguraties. Deze configuraties kunnen vervolgens automatisch worden ingevoerd in Configuration Manager als grenslocaties.  

 Als u uw netwerktopologie te detecteren wilt, moet u netwerkdetectie gebruikt. Hoewel andere detectiemethoden informatie betrekking hebben op Active Directory Domain Services en de huidige netwerklocatie van een client kunt identificeren geretourneerd, bieden ze geen informatie over de infrastructuur op basis van de subnetten en de routertopologie van uw netwerk.  

##  <a name="bkmk_shared"></a>Detectiegegevens gedeeld tussen sites  
 Nadat de gegevens van de detectie Configuration Manager toegevoegd aan een database, worden ze vlug gedeeld tussen alle sites in de hiërarchie. Omdat er meestal geen voordeel voor het detecteren van dezelfde informatie op meerdere sites in uw hiërarchie, kunt u één exemplaar van elke detectiemethode die u gebruikt om uit te voeren op één site. Er is een goed idee om dit te doen in plaats van meerdere exemplaren van één enkele methode uitgevoerd op verschillende sites.  

 Echter, voor bepaalde omgevingen deze nuttig kan zijn om toe te wijzen dezelfde detectiemethode om uit te voeren op meerdere sites, elk met een afzonderlijke configuratie en planning. Wanneer u netwerkdetectie gebruikt, wilt u mogelijk directe van elke site voor het detecteren van het lokale netwerk, in plaats van poging netwerklocaties te detecteren alle via een WAN.

Als u meerdere exemplaren van de dezelfde detectiemethoden worden uitgevoerd op verschillende sites configureert, moet u zorgvuldig plannen de configuratie van elke site. U wilt voorkomen dat twee of meer sites dezelfde bronnen van uw netwerk of Active Directory detecteren. Dit kan aanzienlijk meer netwerkbandbreedte gebruiken en dubbele DDR's creëren.

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

 Wanneer secundaire sites netwerkdetectie uitvoeren of Heartbeat-detectie DDR's ontvangen, dragen ze de DDR door replicatie op basis van bestanden naar hun bovenliggende primaire site. Dit is omdat alleen primaire sites en centrale beheersites DDR's kunnen verwerken. Zie voor meer informatie over hoe DDR's verwerkt [Detectiegegevensrecords](../../../../core/servers/deploy/configure/run-discovery.md#BKMK_DDRs).  

## <a name="considerations-for-different-discovery-methods"></a>Overwegingen voor de verschillende detectiemethoden  
 Omdat elke site en elke netwerkomgeving verschillend is, is het een goed idee om uw eerste configuraties voor de detectie te beperken. Vervolgens controleren nauw elke siteserver voor de mogelijkheid om te verwerken van de detectiegegevens die wordt gegenereerd.  

Als u werkt met een **Active Directory** detectiemethode van systemen, gebruikers of groepen:  

-   Detectie uitvoeren op een site waarop een snelle netwerkverbinding naar uw domeincontrollers.  

-   Houd rekening met de Active Directory-replicatietopologie om ervoor te zorgen detectie toegang tot de meest recente informatie.  

-   Overweeg het bereik van de detectieconfiguratie en beperken van detectie kan alleen de Active Directory-locaties en groepen die u moet detecteren.  

Als u **netwerkdetectie**:  

-   Gebruik een beperkte initiële configuratie om te identificeren van uw netwerktopologie.  

-   Nadat u uw netwerktopografie hebt geïdentificeerd, Stel u netwerkdetectie om uit te voeren op specifieke sites die bepalend zijn voor de netwerkgebieden die u wilt meer volledig detecteren.  

Omdat **Heartbeat-detectie** kan niet worden uitgevoerd op een specifieke site, er geen in rekening brengen in de algemene planning van de locaties waar detectie moet worden uitgevoerd.  

##  <a name="bkmk_best"></a>Aanbevolen procedures voor detectie  
Voor de beste resultaten met detectie raden we het volgende:

 - **Active Directory-Systeemdetectie en Active Directory-Gebruikersdetectie uitvoeren voordat u Active Directory-Groepsdetectie uitvoert.**  

 Als detectie van Active Directory-groepen een eerder gedetecteerde gebruiker of computer als lid van een groep identificeert, wordt geprobeerd om basic details voor de gebruiker of computer te detecteren. Omdat detectie van Active Directory-groepen niet geoptimaliseerd is voor dit type detectie, kan dit proces langzaam veroorzaken. Bijkomend identificeert detectie van Active Directory-groepen enkel de Basisdetails over gebruikers en computers detecteert, en maakt niet een volledige gebruiker of computer detectierecord. Wanneer u Active Directory-Systeemdetectie en Active Directory-Gebruikersdetectie uitvoert, zijn de extra Active Directory-kenmerken voor elk object beschikbaar. Als gevolg hiervan Active Directory Group Discovery efficiënter uitgevoerd.  

- **Bij het instellen van de detectie van Active Directory-groepen, alleen groepen opgeven die u met Configuration Manager gebruikt.**  

 Het gebruik van bronnen door detectie voor Active Directory-groepen, opgeven om te bepalen alleen de groepen die u gebruikt met Configuration Manager. Dit is omdat detectie van Active Directory-groepen recursief elke groep die ze voor gebruikers, computers en geneste groepen detecteert doorzoekt. Het doorzoeken van elke geneste groep kan het bereik van detectie van Active Directory-groepen uitbreiden en prestaties beperken. Bovendien bij het instellen van detectie van verschillen voor detectie van Active Directory-groepen, controleert de detectiemethode elke groep op wijziging. Dit vermindert verder de prestaties wanneer de methode onnodige groepen moet doorzoeken.  

- **Instellen van detectiemethoden met een langer interval tussen volledige detecties, en een frequentere periode voor detectie van verschillen.**  

 Omdat detectie van verschillen minder bronnen dan een volledige detectiecyclus gebruikt en nieuwe of gewijzigde bronnen in Active Directory kunt identificeren, kunt u Verlaag de frequentie van volledige detectiecycli wekelijks moeten worden uitgevoerd (of minder). Detectie van verschillen voor Active Directory-Systeemdetectie, Active Directory-Gebruikersdetectie en detectie van Active Directory-groepen identificeert bijna alle de wijzigingen van Active Directory-objecten en kan nauwkeurige detectiegegevens voor bronnen behouden.  

- **Active Directory-detectiemethoden worden uitgevoerd op een primaire site met een netwerklocatie bevindt die zich het dichtst bij uw Active Directory-domeincontroller.**  

 Ter verbetering van de prestaties van de detectie van Active Directory, het een goed idee om uit te voeren detecteren op een primaire site heeft die een snel netwerkverbinding met uw domeincontrollers. Als u dezelfde detectiemethode voor Active Directory op meerdere sites uitvoert, instellen u elke detectiemethode voor erop overlapping te vermijden. In tegenstelling tot vorige versies van Configuration Manager detectiegegevens gedeeld tussen sites. Het is daarom niet nodig om te detecteren op meerdere sites dezelfde informatie. Zie voor meer informatie [detectiegegevens gedeeld tussen sites](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md#bkmk_shared).  

- **Detectie van Active Directory-Forest op slechts één site uitvoeren wanneer u van plan bent automatisch grenzen te maken van de detectiegegevens.**  

 Als u Active Directory-Forestdetectie op meer dan één site in een hiërarchie uitvoert, is het een goed idee alleen opties voor automatisch grenzen te maken op een enkele site inschakelen. Dit is omdat wanneer Active Directory-Forestdetectie op elke site uitvoert en ze grenzen maakt, Configuration Manager deze grenzen niet in één enkel grensobject samenvoegen. Wanneer u detectie van Active Directory-Forest automatisch grenzen te maken op meerdere sites configureert, zijn het resultaat dat dubbele grensobjecten zijn in de Configuration Manager-console.  
