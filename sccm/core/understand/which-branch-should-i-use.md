---
title: Welke vertakking moet ik gebruiken | Microsoft-documenten
description: Informatie over de verschillen tussen beschikbare vertakkingen van System Center Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: f791278b0aa8efc734a894da7dab1704bb567ed0
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Welke vertakking van Configuration Manager moet ik gebruiken?

*Van toepassing op: System Center Configuration Manager (huidige vertakking op lange termijn onderhoud vertakking en Technical Preview)*


In oktober van 2016 vanaf worden zijn er drie vertakkingen van System Center Configuration Manager beschikbaar. Gebruik dit onderwerp om te helpen de juiste vertakking kiezen voor u.

> [!TIP]  
> Alle sites in een hiërarchie moeten dezelfde vertakking worden uitgevoerd. Een hiërarchie hebt met andere vertakkingen op verschillende sites wordt niet ondersteund.

## <a name="current-branch-of-system-center-configuration-manager"></a>Huidige vertakking van System Center Configuration Manager
Dit is een licentie voor gebruik in een productieomgeving waar u de optie voor het ophalen van de nieuwste functies en functionaliteiten vertakking wordt weergegeven. Dit is de vertakking gebruiken als u een van de volgende: System Center Datacenter, System Center Standard, System Center Configuration Manager of gelijkwaardige abonnementsrechten. Zie voor meer informatie over Software Assurance en het licentie-opties, [volumelicenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).


>  [!TIP]
> De huidige vertakking kan worden geïnstalleerd als een evaluatie-editie die geen licentie vereist. Een evaluatie-editie voor 180 dagen kan worden gebruikt en ondersteunt het upgraden naar een gelicentieerde versie van de huidige vertakking.

De huidige vertakking is meerdere keren per jaar met nieuwe functies bijgewerkt. Elke updateversie wordt ondersteund voor een jaar na de release. U moet bijwerken naar een nieuwere versie van de huidige vertakking op of vóór de vervaldatum van die periode één jaar. Updates voor nieuwe versies zijn beschikbaar als console updates.

U gebruikt voor het installeren van de huidige vertakking als een nieuwe site of als een upgrade van System Center 2012 Configuration Manager met Service Pack 2 of System Center 2012 R2 Configuration Manager met Service Pack 1, [basislijn media](/sccm/core/servers/manage/updates#baseline-and-update-versions) voor System Center Configuration Manager die wordt geleverd als een DVD met System Center 2016 of die beschikbaar is als onderdeel van een zelfstandige versie van System Center Configuration Manager. Toegang tot deze media, is afhankelijk van hoe u een licentie hebt System Center Configuration Manager. Basislijn hoger, zoals 1702 bieden geen ondersteuning voor installatie van de LTSB.

U kunt ook de basislijn media gebruiken voor het installeren van een nieuwe site die een evaluatie-editie van de huidige vertakking wordt weergegeven. Als u wilt dat alleen een evaluatie-editie te installeren, krijgt u software uit de [TechNet-Evaluatiecentrum](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) website.

>  [!NOTE]
> Basislijn media gebruiken om sites te installeren voor een nieuwe Configuration Manager-hiërarchie. Als u eerder een versie van de basislijn zoals versie 1511 hebt geïnstalleerd, gebruikt u in de console-updates bij te werken van uw sites naar een nieuwe versie, zoals 1606.
>
> Sites die zijn bijgewerkt met-console updates resultaat op sites die zijn hetzelfde als de nieuwe site geïnstalleerd met behulp van de basislijn-media.
>
> Zie voor meer informatie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates).

**Functies van de huidige vertakking**
- Ontvangt [in de console-updates](/sccm/core/servers/manage/install-in-console-updates) die nieuwe functies beschikbaar maken voor gebruik.
- In de console-updates die beveiligings- en kwaliteit oplossingen aan bestaande functies leveren ontvangt.
- Biedt ondersteuning voor out-of-band-updates wanneer dat nodig is. Zie [de registratie update Tool](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) of [de hotfixinstallatieprogramma gebruiken dat](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- Kunnen samenwerken met Microsoft Intune en andere services cloud-gebaseerde en infrastructuur.
- Ondersteunt [migratie van gegevens](/sccm/core/migration/migrate-data-between-hierarchies) naar en van andere Configuration Manager-installaties.
- Ondersteuning voor een upgrade van eerdere versies van Configuration Manager.
- Ondersteunt de installatie als een evaluatie-editie van waaruit u later naar een volledig gelicentieerde installatie bijwerken kunt.

De initiële versie van de huidige vertakking is versie 1511. Daaropvolgende updates omvatten versie 1602, 1606, enzovoort. Elke versie blijft in ondersteuning voor één jaar en Microsoft raadt aan dat u naar de nieuwste versie kort na de release bijwerkt. U kunt maximaal één jaar voordat u bijwerkt naar een nieuwere versie wachten en kunt u ook een update voor het installeren van de nieuwste versie beschikbaar overslaan. Omdat elke versie van cumulatieve, als u een update overslaan en installeer de nieuwste versie, worden er nog steeds toegang tot alle functies en verbeteringen ten opzichte van eerdere versies.

Zie voor meer informatie [ondersteuning voor versies van de huidige vertakking](/sccm/core/servers/manage/current-branch-versions-supported).

**Opties voor bijwerken**
- Met het actieve Software Assurance, kunt u in het console-updates voor huidige vertakking versies installeren.  
- Er is geen optie voor de huidige vertakking converteren naar een Technical Preview. Technische voorbeelden zijn afzonderlijke installaties die geen licentie vereist.
- Er is geen optie voor uw huidige filiaal converteren naar de langetermijndoelen onderhoud vertakking (LTSB). U moet de huidige vertakking verwijderen en vervolgens de LTSB installeren als een nieuwe installatie.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>Op lange termijn onderhoud vertakking van de configuratie van System Center
Dit is een licentie vertakking voor gebruik in productieomgevingen voor Configuration Manager-klanten die gebruikmaken van de huidige vertakking en waarvoor toegestaan is de Configuration Manager Software Assurance (SA) of gelijkwaardige abonnementsrechten verloopt na 1 oktober 2016. Zie voor meer informatie over Software Assurance en het licentie-opties, [volumelicenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).

De LTSB is gebaseerd op versie 1606. De vertakking ontvangt niet in de console-updates die nieuwe functies te leveren of bestaande mogelijkheden bijwerken. Echter, kritieke beveiligingsproblemen worden gegeven. U moet de versie 1606 gebruiken voor het installeren van de LTSB [basislijn media](/sccm/core/servers/manage/updates#baseline-and-update-versions) die u ontvangt als een DVD met System Center 2016 of System Center Configuration Manager.

Gebruiken om de LTSB als een nieuwe site of als upgrade van een ondersteunde Configuration Manager 2012-site hebt geïnstalleerd, de versie 1606 [basislijn media](/sccm/core/servers/manage/updates#baseline-and-update-versions) die u ontvangt als een DVD met System Center 2016 of release voor System Center Configuration Manager (huidige vertakking en langetermijnbeveiliging onderhoud vertakking 1606). U kunt basislijn media gebruiken om een nieuwe site waarop versie 1606 van de huidige vertakking of een nieuwe site met de vertakking langetermijndoelen onderhoud te installeren.

> [!TIP]  
> Zie voor meer informatie over System Center 2016, [System Center 2016 documentatie](https://technet.microsoft.com/system-center-docs/system-center). Deze documentatie identificeert ook het ophalen van System Center 2016, waarvoor een gebruiksrechtovereenkomst van Microsoft of vergelijkbare rechten.

> Voor System Center Configuration Manager versie 1606 in het Volume Licensing Service Center (VLSC), gaat u naar de **downloadt en -codes** tabblad van het [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), zoekt u naar "configuratie system center" en selecteer **System Center Config Mgr (huidige vertakking en LTSB 1606)**.

> U kunt ook een evaluatieversie van System Center 2016 van krijgen de [TechNet-Evaluatiecentrum](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).

**Functies van de LTSB**
-    In de console-updates met een kritieke beveiligingsproblemen compleet ontvangt
- Biedt een installatieoptie selecteren wanneer uw SA-overeenkomst of vergelijkbare rechten voor Configuration Manager zijn verlopen
- Ondersteuning voor een upgrade (conversie) op de vertakking van de huidige als er een huidige Software Assurance-overeenkomst of vergelijkbare rechten voor Configuration Manager

**Beperkingen**  
De LTSB is gebaseerd op de huidige vertakking versie 1606 en heeft de volgende beperkingen:
- De LTSB wordt ondersteund voor tien jaar essentiële beveiligingsupdates na de algemene beschikbaarheid (oktober van 2016), na welke, ondersteuning voor de vertakking verloopt. Zie voor meer informatie over de levenscyclus van ondersteuning [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).
- Ondersteunt een beperkte set-lijst van de server en client-besturingssystemen en verwante technologieën, zoals SQL Server-versies. Zie voor meer informatie over wat er met de vertakking wordt ondersteund, [ondersteunde configuraties voor de vertakking langetermijndoelen onderhoud](supported-configurations-for-ltsb.md).
- Ontvangt geen updates voor de nieuwe functies.
- Biedt geen ondersteuning voor het toevoegen van een Microsoft Intune-abonnement, die voorkomt het gebruik van dat:
  -    Intune in een hybride MDM-configuratie
 - On-premises MDM
-    Biedt geen ondersteuning voor gebruik van de Windows 10 onderhoud Dashboard, onderhoud plannen, Windows 10 huidige vertakking (CB) of huidige vertakking voor Business (CBB).
- Biedt geen ondersteuning voor toekomstige versies van Windows 10 LTSB en Windows Server.
-    Er is geen ondersteuning voor Asset Intelligence.
-    Er is geen ondersteuning voor cloud-gebaseerde distributiepunten.
-    Er is geen ondersteuning voor de ondersteuning voor Exchange Online als een Exchange-Connector.
-    Biedt geen ondersteuning voor een voorlopige versie van de functies.



**Opties voor bijwerken**
- U kunt de installatie LTSB omzetten in een installatie van de huidige vertakking. Conversie naar de huidige vertakking wordt ondersteund voor of na de ondersteuning voor de LTSB verloopt.

  Als u wilt converteren, moet u een actief Software Assurance-overeenkomst met Microsoft hebben. Zie de volgende koppelingen voor meer informatie:
  - [De lange termijn Servicing vertakking bijwerken naar de huidige vertakking](convert-to-current-branch.md)
  - [Licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md)
  - [Basislijn en update versies](/sccm/core/servers/manage/updates#baseline-and-update-versions) in [Updates voor Configuration Manager](/sccm/core/servers/manage/updates)
- Er is geen optie de LTSB converteren naar een Technical Preview. Technische voorbeelden zijn afzonderlijke installaties die geen licentie vereist.
-    U upgraden een evaluatie-editie van de huidige vertakking wordt weergegeven met een LTSB-installatie niet.


## <a name="technical-preview-for-system-center-configuration-manager"></a>Technical Preview voor System Center Configuration Manager
Technische Preview is voor gebruik in een testomgeving waar u meer informatie over en probeer de nieuwste functies wordt ontwikkeld voor Configuration Manager uit. Technische Preview wordt niet ondersteund in een productieomgeving en vereist niet dat u hebt een licentieovereenkomst Software Assurance.

Gebruiken voor het installeren van een nieuwe site met de technische Preview van de meest recente [basislijn media voor de System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). Na installatie van de technische Preview van zijn nieuwe versies beschikbaar als console updates iedere maand.

**Functies van de Technical Preview**
-  Op basis van recente basislijn versies van de huidige vertakking
-  In de console-updates die de installatie van de update naar de nieuwste technische Preview-versie ontvangt
-  Bevat nieuwe functies die worden ontwikkeld en onze ontwikkelaars wilt waarvoor uw feedback
-  Updates die alleen van toepassing op de vertakking Technical Preview ontvangt

**Beperkingen**
-  [Ondersteuning is beperkt](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), met inbegrip van slechts een enkele primaire site en maximaal 10 clients.  
-  Kan niet worden bijgewerkt naar een huidige filiaal of LTSB.
-  Ondersteunt geen migratie gebruiken om te importeren of gegevens exporteren naar een andere Configuration Manager-installatie.
-  Ondersteunt geen upgrade van een eerdere versie van Configuration Manager.
-  Biedt geen ondersteuning voor installatie als een evaluatie-editie.

Functies die zijn geïntroduceerd in een Technical Preview worden vaak toegevoegd aan de huidige vertakking hoger bij te werken. Elke nieuwe Technical Preview-versie bevat de functies van de vorige technische voorbeelden, zelfs nadat deze functies zijn toegevoegd aan de huidige vertakking.

Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).

**Opties voor bijwerken**
-    U kunt een update in de console voor een nieuwe Technical Preview-versie installeren.
-    Er is geen optie Technical Preview converteren naar het huidige filiaal of LTSB.


## <a name="identify-your-branch-and-version"></a>De vertakking en versie bepalen
Wanneer u versie-informatie voor een Configuration Manager-site weergeven, controleert u ook de vertakking.

**Versie**   
Controleer de versie van uw site in de console Ga naar de **over System Center Configuration Manager** op de linkerbovenhoek van de console waar de **siteversie** wordt weergegeven. Zie [ ]() voor een lijst met versies van de site.

**Filiaal**  
Bevestig de vertakking van uw site (als de LTSB of de huidige vertakking), in de console gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. Als er een optie converteren naar de huidige vertakking wordt weergegeven en ze actief is, voert de site de LTSB-versie. Wanneer de site wordt uitgevoerd de huidige vertakking, deze optie is niet beschikbaar.
Zie voor informatie over de verschillende versies van Configuration Manager "basislijn en update versies" in [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).

