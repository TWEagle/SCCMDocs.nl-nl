---
title: Welke vertakking moet ik gebruiken
titleSuffix: Configuration Manager
description: Meer informatie over de verschillen tussen de beschikbare vertakkingen van System Center Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
caps.latest.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fb72cf0a2982fe4cbefd63e8ae27d169066557c2
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Welke vertakking van Configuration Manager moet ik gebruiken?

*Van toepassing op: System Center Configuration Manager (huidige vertakking, op lange termijn Servicing Branch en Technical Preview)*


Vanaf oktober 2016 kan zijn er drie vertakkingen van System Center Configuration Manager beschikbaar. Gebruik dit onderwerp om u te helpen bij het kiezen van de juiste vertakking voor u.

> [!TIP]  
> Alle sites in een hiërarchie moeten dezelfde tak uitvoeren. Een hiërarchie hebt met verschillende filialen op verschillende sites wordt niet ondersteund.

## <a name="current-branch-of-system-center-configuration-manager"></a>Huidige vertakking van System Center Configuration Manager
Dit is een vertakking een licentie voor gebruik in een productieomgeving waar u de optie voor het ophalen van de nieuwste functies en functionaliteiten. Dit is de vertakking kunt gebruiken als u een van de volgende: System Center-Datacenter, System Center Standard, System Center Configuration Manager of gelijkwaardige abonnementsrechten. Zie voor meer informatie over Software Assurance en licentie-opties [licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).


>  [!TIP]
> De huidige vertakking kan worden geïnstalleerd als een evaluatie-editie die geen licentie vereist. Een evaluatieversie voor 180 dagen kan worden gebruikt en het ondersteunt een upgrade uit naar een gelicentieerde versie van de huidige vertakking.

De huidige vertakking is meerdere keren een jaar met nieuwe functies worden bijgewerkt. Elke versie van de update wordt ondersteund voor een jaar na de release. U moet bijwerken naar een nieuwere versie van de huidige vertakking op of vóór de vervaldatum van die periode van één jaar. Updates naar nieuwere versies zijn beschikbaar als console-updates.

U gebruikt voor het installeren van de huidige vertakking als een nieuwe site of als een upgrade van System Center 2012 Configuration Manager met Service Pack 2 of System Center 2012 R2 Configuration Manager met Service Pack 1, [basislijnmedia](/sccm/core/servers/manage/updates#baseline-and-update-versions) voor System Center Configuration Manager die wordt geleverd als een DVD met System Center 2016 of die beschikbaar is als onderdeel van een zelfstandige versie van System Center Configuration Manager. Toegang tot deze media is afhankelijk van hoe u een licentie hebt System Center Configuration Manager. Basislijn hoger, zoals 1702 bieden geen ondersteuning voor installatie van de LTSB.

U kunt ook de basislijnmedia gebruiken voor het installeren van een nieuwe site die een evaluatie-editie van de huidige vertakking. Als u installeren, alleen een evaluatie-editie wilt, kunt u software van de [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) website.

>  [!NOTE]
> Basislijnmedia gebruiken om sites te installeren voor een nieuwe Configuration Manager-hiërarchie. Als u een basislijnversie zoals versie 1511 eerder hebt geïnstalleerd, gebruikt u updates in de console voor het bijwerken van uw sites naar een nieuwe versie, zoals 1606.
>
> Sites die zijn bijgewerkt met in-console updates leiden tot sites die zijn hetzelfde als de nieuwe site geïnstalleerd met behulp van de basislijnmedia.
>
> Zie voor meer informatie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates).

**Functies van de huidige vertakking**
- Ontvangt [updates in de console](/sccm/core/servers/manage/install-in-console-updates) zodat nieuwe functies beschikbaar zijn voor gebruik.
- In de console-updates die beveiligings- en kwaliteit-oplossingen aan bestaande functies leveren ontvangt.
- Biedt ondersteuning voor out-of-band-updates wanneer dit nodig. Zie [gebruik het hulpprogramma registratie bijwerken](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) of [gebruiken het hotfix-installatieprogramma](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- Kan samenwerken met Microsoft Intune en andere cloudservices en -infrastructuur.
- Ondersteunt [migratie van gegevens](/sccm/core/migration/migrate-data-between-hierarchies) naar en van andere Configuration Manager-installaties.
- Ondersteuning voor een upgrade van eerdere versies van Configuration Manager.
- Ondersteunt de installatie als een evaluatie-editie die u later naar een volledig gelicentieerde installatie kunt upgraden.

De initiële versie van de huidige vertakking is versie 1511. Daaropvolgende updates omvatten versie 1602 1606, enzovoort. Elke versie blijft in de ondersteuning voor één jaar en Microsoft raadt u aan bij te werken naar de nieuwste versie kort na de release. U kunt maximaal één jaar voordat u bijwerkt naar een nieuwere versie wachten en u kunt ook een update voor het installeren van de nieuwste versie beschikbaar overslaan. Omdat elke versie cumulatief, als u een update overslaan en installeer de nieuwste versie, worden er nog steeds toegang tot alle functies en verbeteringen van eerdere versies.

Zie voor meer informatie [ondersteuning voor versies van de huidige vertakking](/sccm/core/servers/manage/current-branch-versions-supported).

**Opties voor het bijwerken**
- Met het actieve Software Assurance, kunt u updates in de console voor versies van de Current Branch installeren.  
- Er is geen optie in de huidige vertakking converteren naar een Technical Preview. Technical Previews zijn afzonderlijke installaties die geen licentie vereist.
- Er is geen optie converteren van uw huidige vertakking naar de Long-Term Servicing Branch (LTSB). U moet de huidige vertakking verwijderen en vervolgens de LTSB installeren als een nieuwe installatie.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>Op lange termijn onderhoud vertakking van System Center Configuration
Dit is een vertakking een licentie voor gebruik in productie voor Configuration Manager-klanten die gebruikmaken van de huidige vertakking en waarvoor toegestaan is hun Configuration Manager Software Assurance (SA) of een equivalente abonnementsrechten verlopen na 1 oktober 2016. Zie voor meer informatie over Software Assurance en licentie-opties [licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).

De LTSB is gebaseerd op versie 1606. De vertakking ontvangt geen in de console-updates die nieuwe functies te leveren of bestaande mogelijkheden bijwerken. Evenwel, kritieke beveiligingsproblemen zijn verleend. Als u wilt de LTSB installeren, moet u de versie 1606 [basislijnmedia](/sccm/core/servers/manage/updates#baseline-and-update-versions) die u krijgt als een DVD met System Center 2016 of System Center Configuration Manager.

U kunt de LTSB installeren als een nieuwe site of als een upgrade van een ondersteunde Configuration Manager 2012-site met de versie 1606 [basislijnmedia](/sccm/core/servers/manage/updates#baseline-and-update-versions) die u krijgt als een DVD met System Center 2016 of release van System Center Configuration Manager (huidige vertakking en Long-Term Servicing Branch 1606). U kunt basislijnmedia gebruiken voor het installeren van een nieuwe site met versie 1606 van de huidige vertakking of een nieuwe site die de vertakking Long-Term onderhoud wordt uitgevoerd.

> [!TIP]  
> Zie voor meer informatie over System Center 2016, [System Center 2016 documentatie](https://technet.microsoft.com/system-center-docs/system-center). Deze documentatie identificeert ook System Center 2016, waarvoor een gebruiksrechtovereenkomst van Microsoft of soortgelijke rechten krijgen.

> Als u in het Volume Licensing Service Center (VLSC) voor System Center Configuration Manager versie 1606 zoekt, gaat u naar de **downloadt en -sleutels** tabblad van de [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), zoek naar "system center-config" en selecteer vervolgens **System Center Config Mgr (huidige vertakking en LTSB)**.

> U kunt ook een evaluatieversie van System Center 2016 van krijgen de [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).

**Functies van de LTSB**
-   In de console-updates die kritieke beveiligingsproblemen leveren ontvangt
- Biedt een installatieoptie wanneer uw SA overeenkomst of een vergelijkbare rechten aan Configuration Manager zijn verlopen
- Ondersteuning voor een upgrade (conversie) naar de huidige vertakking als er een huidige SA agreement of equivalente rechten aan Configuration Manager

**Beperkingen**  
De LTSB is gebaseerd op de huidige vertakking versie 1606 en heeft de volgende beperkingen:
- De LTSB wordt ondersteund voor tien jaar van essentiële beveiligingsupdates na de algemene beschikbaarheid (oktober 2016), na welke, ondersteuning voor de vertakking verloopt. Zie voor meer informatie over de levenscyclus voor ondersteuning, [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).
- Ondersteunt een beperkte set-lijst van de server en client-besturingssystemen en verwante technologieën, zoals SQL Server-versies. Zie voor meer informatie over wat wordt ondersteund met de vertakking [ondersteunde configuraties voor de vertakking Long-Term onderhoud](supported-configurations-for-ltsb.md).
- Ontvangt geen updates voor de nieuwe functies.
- Biedt geen ondersteuning voor het toevoegen van een Microsoft Intune-abonnement, waardoor het gebruik van:
  - Intune in een hybride MDM-configuratie
 - On-premises MDM
-   Biedt geen ondersteuning voor gebruik van de Windows 10-Onderhoudsdashboard, onderhoud plannen, Windows 10 Current Branch (CB) of Current Branch for Business (CBB).
- Biedt geen ondersteuning voor toekomstige versies van Windows 10 LTSB en Windows Server.
-   Er is geen ondersteuning voor Asset Intelligence.
-   Er is geen ondersteuning voor cloud-gebaseerde distributiepunten.
-   Er is geen ondersteuning voor de ondersteuning voor Exchange Online als een Exchange-Connector.
-   Ondersteunt niet alle functies van evaluatieversies.



**Opties voor het bijwerken**
- U kunt de installatie van de LTSB converteren naar een Current Branch-installatie. Conversie naar de huidige vertakking wordt ondersteund voor of na ondersteuning voor de LTSB verloopt.

  Als u wilt converteren, moet u een actieve Software Assurance-overeenkomst met Microsoft hebben. Zie de volgende koppelingen voor meer informatie:
  - [De Long-Term Servicing Branch upgraden naar de Current Branch](convert-to-current-branch.md)
  - [Licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md)
  - [Basislijn- en updateversies](/sccm/core/servers/manage/updates#baseline-and-update-versions) in [Updates voor Configuration Manager](/sccm/core/servers/manage/updates)
- Er is geen optie de LTSB converteren naar een Technical Preview. Technical Previews zijn afzonderlijke installaties die geen licentie vereist.
-   U kunt een evaluatieversie van de huidige vertakking niet bijwerken naar een LTSB-installatie.


## <a name="technical-preview-for-system-center-configuration-manager"></a>Technical Preview voor System Center Configuration Manager
De Technical Preview is voor gebruik in een testomgeving waar u meer informatie over en de nieuwste functies wordt ontwikkeld voor Configuration Manager uit te proberen. De Technical Preview wordt niet ondersteund in een productieomgeving en vereist niet dat u hebt een licentieovereenkomst van Software Assurance.

U kunt een nieuwe site met de Technical Preview installeren met de meest recente [basislijnmedia voor de System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). Nadat u de Technical Preview hebt geïnstalleerd, zijn nieuwe versies beschikbaar als console-updates iedere maand.

**Functies van de Technical Preview**
-  Op basis van recente basislijnversies van de huidige vertakking
-  Ontvangt in de console-updates die uw installatie naar de nieuwste versie van de Technical Preview bijwerken
-  Bevat nieuwe functies die worden ontwikkeld en onze ontwikkelaars wilt waarvoor uw feedback
-  Updates die alleen van toepassing op de Technical Preview vertakking ontvangt

**Beperkingen**
-  [Ondersteuning is beperkt](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), met inbegrip van slechts één primaire site en maximaal 10 clients.  
-  Kan niet worden bijgewerkt naar een Current Branch of LTSB.
-  Ondersteunt geen migratie gebruiken om te importeren of gegevens exporteren naar een andere Configuration Manager-installatie.
-  Ondersteunt geen upgrade van een eerdere versie van Configuration Manager.
-  Biedt geen ondersteuning voor installatie als een evaluatie-editie.

Functies die zijn geïntroduceerd in een Technical Preview zijn vaak toegevoegd aan de huidige vertakking in een latere update. Elke nieuwe technische Preview-versie bevat de functies van de vorige technical Previews worden geboden, zelfs nadat deze functies zijn toegevoegd aan de huidige vertakking.

Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).

**Opties voor het bijwerken**
-   U kunt een update in de console voor een nieuwe versie van de Technical Preview installeren.
-   Er is geen optie een Technical Preview converteren naar de huidige vertakking of LTSB.


## <a name="identify-your-branch-and-version"></a>Identificeer uw vertakking en versie
Als u versie-informatie voor een Configuration Manager-site bekijkt, worden ook de vertakking bevestigen.

**Versie**   
Controleer de versie van uw site in de console Ga naar de **over System Center Configuration Manager** op de linkerbovenhoek van de console waar de **siteversie** wordt weergegeven. Zie [basislijn- en updateversies](/sccm/core/servers/manage/updates#bkmk_Baselines) voor een lijst met versies van de site.

**Filialen**  
Om te bevestigen dat de vertakking van uw site (als de LTSB of Current Branch) in de console gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. Als er een optie om te converteren naar de huidige vertakking en actief is, voert de site de LTSB-versie. Wanneer de site wordt uitgevoerd de huidige vertakking, wordt deze optie grijs weergegeven. Zie voor informatie over de verschillende versies van Configuration Manager 'basislijn- en updateversies' [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).
