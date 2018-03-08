---
title: Technische Preview-versies
titleSuffix: Configuration Manager
description: Meer informatie over de Technical Preview-versie dat we u test-drive nieuwe functionaliteit en mogelijkheden in System Center Configuration Manager.
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 1cb4d775985839ea7c4fb1b48a04ab0be64f5d8c
ms.sourcegitcommit: 32bbc006a41868a6d9a708db5f7b372d9c71d985
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/08/2018
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Technical Preview voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

**Welkom bij de System Center Configuration Manager Technical Preview**. In dit artikel bevat informatie over de zich ontwikkelende preview-versie die introduceert nieuwe functionaliteit en mogelijkheden bieden die we aan werken. Elke versie van de technical preview introduceert nieuwe functies die niet zijn opgenomen in de huidige vertakking van Configuration Manager op het moment dat de technische preview-versie beschikbaar wordt gesteld. Deze functies worden uiteindelijk misschien opgenomen in een update van de huidige release, maar voordat we de functies voltooien en toevoegen, willen we u de mogelijkheid bieden ze uit te proberen en ons feedback te geven.  

 Omdat deze release een technical preview is, nog details en functionaliteit worden gewijzigd.  

 In dit artikel bevat informatie die van toepassing op alle versies van de Technical Preview. Het bevat ook elke nieuwe mogelijkheid (of functie) samen met de technische Preview-versie waarin de mogelijkheid eerst wordt weergegeven, zoals versie 1802 voor februari van 2018. Deze mogelijkheden worden beschreven in afzonderlijke onderwerpen elke preview-versie.  

 Zie voor meer informatie over wat er nieuw in de huidige vertakking van Configuration Manager [wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Voorwaarden en beperkingen voor de Technical Preview  

> [!IMPORTANT]     
>  Een licentie voor een Technical Preview wordt alleen gegeven voor gebruik in een testomgeving.  Microsoft kan geen ondersteuningsdiensten en bepaalde functies zijn mogelijk niet beschikbaar in de preview-software. Bovendien de preview-software mogelijk lager of andere standaarden voor de beveiliging, privacy, toegankelijkheid, beschikbaarheid en betrouwbaarheid ten opzichte commerciële software opgegeven.  

 Gebruik de informatie in de meeste productvereisten de [ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). De volgende uitzonderingen zijn van toepassing op de Technical Preview-versies:  

-   Elke installatie blijft gedurende 90 dagen actief, daarna wordt deze inactief.  

-   Engels is de enige ondersteunde taal.


-   Alleen de volgende installatievlaggen (schakelopties) worden ondersteund:  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Wanneer u de technical preview installeert het serviceverbindingspunt wordt gehost op de onlinemodus. Het ondersteunt niet wijzigen naar de offlinemodus.

-   De afzonderlijke artikelen voor elke specifieke versie van de technical preview zijn extra beperkingen of vereisten, indien van toepassing.

-   Er is geen ondersteuning voor migratie naar of van deze preview-versie.  

-   Er is geen ondersteuning voor het upgraden naar deze preview-versie. 

-   Er is geen ondersteuning voor herstel van sites in de map cd.latest.  <!--507106-->

-   Er is geen ondersteuning voor het upgraden naar een productieversie (huidige vertakking) vanuit deze preview-versie. Echter, wanneer updates beschikbaar voor een preview-versie zijn, kunt u vinden en installeren uit de **Updates en onderhoud** knooppunt van de Configuration Manager-console. Zie [ConfigMgr-updatepakketten installeren](https://www.youtube.com/embed/KBd_EGFbUT8) op youtube.com voor een video van het upgradeproces in de console.  
-   Alleen zelfstandige primaire sites worden ondersteund. Er is geen ondersteuning voor centrale beheersites, meerdere primaire sites en secundaire sites.  

De volgende producten en technologieën worden ondersteund door deze vertakking van Configuration Manager. Ze zijn opgenomen in deze inhoud betekent echter niet dat een uitbreiding van ondersteuning voor een product of een versie die is levenscyclus van dat product afzonderlijke ondersteuning. Producten waarvan de levenscyclus van de ondersteuning worden niet ondersteund voor gebruik met Configuration Manager. Ga naar de website [Microsoft Support Lifecycle](http://go.microsoft.com/fwlink/p/?LinkId=208270) voor meer informatie over Microsoft Support-levenscycli.  

-   Alleen de volgende versies van SQL Server worden ondersteund:  

    -   SQL Server 2017 (met cumulatieve update 2 en hoger) met ingang van Configuration Manager versie 1710
    -   SQL Server 2016 (zonder servicepack en hoger)
    -   SQL Server 2014 (met Service Pack 1 of hoger)
    -   SQL Server 2012 (met Service Pack 3 of hoger)


-   De site ondersteunt maximaal 10 clients waarop een van de volgende versies van Windows moeten worden uitgevoerd:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 7  

##  <a name="bkmk_install"></a> De Technical Preview installeren en bijwerken  
 De System Center Configuration Manager Technical Preview is verschillend van de huidige release van System Center Configuration Manager.  

 Voor het gebruik van de technical preview, moet u eerst installeren een **basislijnversie** van de technical preview-build. Wanneer u een basislijnversie hebt, gebruikt u vervolgens **updates in de console** om uw installatie up-to-date blijven met de meest recente preview-versie. Normaal gesproken wordt er elke maand een nieuwe versie van de Technical Preview beschikbaar.

Elke preview-versie wordt ondersteund totdat drie opeenvolgende versies beschikbaar zijn. Dit betekent dat wanneer versie 1708 uitgebracht, versie 1704 niet langer worden ondersteund is, maar versie 1705, 1706 en 1707 bleef worden ondersteund. Wanneer u een basislijn valt niet worden ondersteund, is het nog steeds ondersteund voor het installeren van een nieuwe technische Preview-site totdat een nieuwe basislijnversie beschikbaar, is zolang u die installatie naar een ondersteunde versie bijwerken. Bijwerken naar de meest recente versie en Herhaal dit proces totdat u de meest recente versie van de technical preview kunt installeren.

> [!TIP]  
>  Wanneer u een update installeert voor de Technical Preview, werkt u de preview-installatie bij naar die nieuwe Technische Preview-versie.    De installatie van een preview-versie biedt nooit de optie voor het bijwerken naar een Current Branch-installatie of het ontvangen van updates van de Current Branch-release.  

**Basislijnversies van de Technical Preview activeren:**
   
U kunt een basislijnversie gedurende maximaal één jaar na de release installeren. Wanneer u een nieuwe technische preview-site installeert, is het echter aangeraden te gebruiken van de meest recente basislijnversie die beschikbaar is.
-  **Technische Preview 1711** -de Configuration Manager Technical Preview 1711 is beschikbaar als zowel een in de console-update en als nieuwe basislijnversie. Basislijnversies downloaden [via het TechNet Evaluation Center](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).


##  <a name="BKMK_TPFeedback"></a> Feedback geven  
 We ontvangen graag uw feedback over de mogelijkheden van onze technical Previews worden geboden. Zie voor meer informatie [productfeedback](../understand/find-help.md#product-feedback).

Als u ideeën over nieuwe functies dat zou willen zien hebt, willen we weten dat ook. Als u nieuwe ideeën wilt indienen en wilt stemmen over de ideeën die door anderen zijn ingediend, gaat u naar onze [UserVoice-pagina](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Mogelijkheden die in de meest recente technical preview  
Hieronder vindt u de mogelijkheden die in de meest recente Configuration Manager technical preview-versie.  Mogelijkheden die beschikbaar in een eerdere versie van de technical preview waren blijven beschikbaar in latere versies. Op dezelfde manier de mogelijkheden die zijn toegevoegd aan de huidige vertakking van Configuration Manager blijven beschikbaar in technical preview-versies.  Klik verder naar de inhoud voor elke preview-versie voor meer informatie over een specifieke functie.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1802"></a>Technical Preview versie 1802
- [Overgang Endpoint Protection werkbelasting voor Intune met CO-management](capabilities-in-technical-preview-1802.md#transition-endpoint-protection-workload-to-intune-using-co-management) <!-- 1357365 -->
- [Windows leveringsoptimalisatie voor het gebruik van Configuration Manager-grensgroepen configureren](capabilities-in-technical-preview-1802.md#configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups) <!-- 1324696 --> 
- [Takenreeks Windows 10 in-place upgrade via cloud management gateway](capabilities-in-technical-preview-1802.md#windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway) <!-- 1357149 -->
- [Verbeteringen in de takenreeks Windows 10 in-place upgrade](capabilities-in-technical-preview-1802.md#improvements-to-windows-10-in-place-upgrade-task-sequence) <!-- 1357425 --> 
- [Verbeteringen aan distributiepunten met PXE-functionaliteit](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) <!-- 1357580 --> 
- [Implementatiesjablonen voor takenreeksen](capabilities-in-technical-preview-1802.md#deployment-templates-for-task-sequences) <!-- 1357391 --> 
- [Product lifecycle-dashboard](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) <!--1319632 --> 
- [Verbeteringen aan te melden](capabilities-in-technical-preview-1802.md#improvements-to-reporting) <!--1357653 --> 
- [Verbeteringen aan Software Center](capabilities-in-technical-preview-1802.md#improvements-to-software-center) <!--1357592 --> 
- [Verbeteringen aan het uitvoeren van Scripts](capabilities-in-technical-preview-1802.md#improvements-to-run-scripts) <!--1236459 --> 
- [Grensgroep voor beheerpunten terugval](capabilities-in-technical-preview-1802.md#boundary-group-fallback-for-management-points) <!-- 1324594 --> 
- [Verbeterde ondersteuning voor CNG-certificaten](capabilities-in-technical-preview-1802.md#improved-support-for-cng-certificates) <!-- 1357314 --> 
- [Ondersteuning voor Azure Resource Manager-gateway cloud](capabilities-in-technical-preview-1802.md#cloud-management-gateway-support-for-azure-resource-manager) <!-- 1324735 --> 
- [Goedkeuren van aanvragen van toepassingen voor gebruikers per apparaat](capabilities-in-technical-preview-1802.md#approve-application-requests-for-users-per-device) <!-- 1357015 --> 
- [Software Center gebruiken om te zoeken en installeren van de gebruiker beschikbare toepassingen op Azure AD-die lid zijn van apparaten](capabilities-in-technical-preview-1802.md#use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices) <!-- 1322613 --> 
- [Rapport over Windows Automatische piloot apparaatgegevens](capabilities-in-technical-preview-1802.md#report-on-windows-autopilot-device-information) <!-- 1351442 --> 
- [Verbeteringen in Configuration Manager-beleid voor Windows Defender misbruiken Guard](capabilities-in-technical-preview-1802.md#improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard) <!-- 1356220 -->
- [Microsoft Edge-browser-beleid](capabilities-in-technical-preview-1802.md#microsoft-edge-browser-policies) <!-- 1357310 -->
- [Rapport voor standaard browser aantallen](capabilities-in-technical-preview-1802.md#report-for-default-browser-counts) <!-- 1357830 --> 
- [Ondersteuning voor Windows 10 ARM64 apparaten](capabilities-in-technical-preview-1802.md#support-for-windows-10-arm64-devices) <!-- 1353704 --> 
- [Wijzigingen in gefaseerde implementaties](capabilities-in-technical-preview-1802.md#changes-to-phased-deployments) <!-- 1357405 -->



## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>Mogelijkheden die in recente ondersteunde technical Previews worden geboden
Hieronder vindt u de mogelijkheden die in eerdere versies van de Configuration Manager technical preview-versie die nog steeds worden ondersteund. 

<!-- This is the full list of new features in the past three TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |Mogelijkheid |Technische Preview-versie |Huidige versie van het filiaal|  
 |----------------|---------------------|--------------------|
 |Gefaseerde implementaties maken <!-- 1357405 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#create-phased-deployments)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Mede management reporting <!-- 1356648 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#co-management-reporting)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Verbeteringen aan automatische implementatie regel evaluatieplanning <!-- 1357133 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-automatic-deployment-rule-evaluation-schedule)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Opnieuw toewijzen van distributiepunt <!-- 1306937 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#reassign-distribution-point)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Verbeteringen in de hardware-inventaris <!-- 1357389 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-hardware-inventory)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Verbeteringen in de clientinstellingen voor Software Center <!-- 1355146 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-client-settings-for-software-center)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Nieuwe instellingen voor Windows Defender toepassing Guard <!-- 1356256 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#new-settings-for-windows-defender-application-guard)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Verbeteringen aan het uitvoeren van Scripts <!-- 1236459 --> | [Tech Preview 1801](capabilities-in-technical-preview-1801.md#improvements-to-run-scripts)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Vervangen van toepassingen niet automatisch bijgewerkt <!-- 1351266 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#do-not-automatically-upgrade-superseded-applications)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Meerdere toepassingen in Software Center installeren <!-- 1357126 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#install-multiple-applications-in-software-center)  |![Niet toegevoegd](media/Red_X.gif)    |
 |PXE-responder-service op basis van client <!-- 1357148 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service)  |![Niet toegevoegd](media/Red_X.gif)    |
 |Wijziging in de Configuration Manager-client installeren <!-- 1356195 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#change-in-the-configuration-manager-client-install)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Wijzig in het dashboard Surface apparaat <!-- 1355788 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#change-to-the-surface-device-dashboard)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Verbeteringen aan beheer van Office 365 Client-dashboard <!-- 1357281 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-office-365-client-management-dashboard)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Verbeteringen in de Configuration Manager-console <!-- 1357280,1357282 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-the-configuration-manager-console)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Verbeteringen in de implementatie van besturingssysteem <!-- SMS 500897 --> | [Tech Preview 1712](capabilities-in-technical-preview-1712.md#improvements-to-operating-system-deployment)  |![Niet toegevoegd](media/Red_X.gif)    | 
 |Takenreeksstap uitvoeren <!-- 1261338 --> | [Tech Preview 1711](capabilities-in-technical-preview-1711.md) |[Versie 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence)    |
 |Interactie van de gebruiker toestaan bij het installeren van een toepassing <!-- 1356976 --> | [Tech Preview 1711](capabilities-in-technical-preview-1711.md) |![Niet toegevoegd](media/Red_X.gif)    |

 

## <a name="capabilities-delivered-in-previous-technical-previews"></a>Mogelijkheden die in vorige technical Previews worden geboden
Hier volgen de specifieke mogelijkheden die in eerdere versies van de Configuration Manager technical preview-versie. Deze mogelijkheden blijven beschikbaar in latere versies, maar nog niet beschikbaar in een current branch-release. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

 |Mogelijkheid |Technische Preview-versie |  
 |----------------|---------------------|
 |Verbeterde VPN-profiel ervaring in Configuration Manager-Console <!-- 1313282 --> | [Tech Preview 1709](capabilities-in-technical-preview-1709.md) |
 |Management insights  <!-- 1353967 --> |[Tech Preview 1708](capabilities-in-technical-preview-1708.md#management-insights)|
 |Surface apparaat dashboard <!-- 1355788 --> |[Tech Preview 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|
 |Beschikbaarheid van de site server-rol <!-- 1128774 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 |Ondersteuning voor PXE-netwerk opstarten voor IPv6 <!-- 1269793 --> |[Tech Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
 |Apparaat Health Attestation beoordeling van van nalevingsbeleid voor voorwaardelijke toegang <!-- 1235616 -->|[Tech Preview 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|
 |Azure Active Directory gebruiken <!-- 1322145? --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
 |Nalevingsbeoordeling voor Windows Update voor bedrijven-updates <!-- 1235390 --> | [Tech Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
 |Toegang tot de gegevens van de OData-eindpunt <!-- 1321523 --> |[Tech Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
 |Verbeteringen in Asset Intelligence <!-- 1307390 --> |[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
 |Eindgebruikers kunnen apps installeren vanuit de bedrijfsportal <!-- 1037233? --> |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|



## <a name="see-also"></a>Zie ook  
[Wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Inleiding op System Center Configuration Manager](../../core/understand/introduction.md)
