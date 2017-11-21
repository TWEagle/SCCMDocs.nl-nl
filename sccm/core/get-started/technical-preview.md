---
title: Technische Preview-versies
titleSuffix: Configuration Manager
description: Meer informatie over de Technical Preview-versie dat we u test-drive nieuwe functionaliteit en mogelijkheden in System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: "157"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: c03581ba5d582d6b86f17c7ec34c3e6e0e8d627e
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Technical Preview voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

**Welkom bij de System Center Configuration Manager Technical Preview**. Dit onderwerp bevat informatie over de preview-versie die in ontwikkeling is en die nieuwe functionaliteit en mogelijkheden introduceert waaraan wij werken. Bij elke versie van de technical preview worden nieuwe functies geïntroduceerd die niet zijn opgenomen in de huidige vertakking van System Center Configuration Manager op het moment dat de technische preview-versie beschikbaar wordt gesteld. Deze functies worden uiteindelijk misschien opgenomen in een update van de huidige release, maar voordat we de functies voltooien en toevoegen, willen we u de mogelijkheid bieden ze uit te proberen en ons feedback te geven.  

 Omdat dit een Technical Preview is, kan het zijn dat de details en functionaliteit nog worden gewijzigd.  

 In dit onderwerp bevat informatie die van toepassing op alle versies van de Technical Preview en vermeldt tevens elke nieuwe mogelijkheid (of functie) samen met de technische Preview-versie waarin de mogelijkheid eerst wordt weergegeven, zoals versie 1710 voor oktober van 2017. De details van deze mogelijkheden worden per preview-versie in afzonderlijke onderwerpen beschreven.  

 Zie voor meer informatie over wat er nieuw in de huidige vertakking van Configuration Manager [wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Voorwaarden en beperkingen voor de Technical Preview  

> [!IMPORTANT]     
>  Een licentie voor een Technical Preview wordt alleen gegeven voor gebruik in een testomgeving.  Microsoft biedt wellicht geen ondersteuningsdiensten en bepaalde functies zijn mogelijk niet beschikbaar in de Preview-software. Daarnaast is het mogelijk dat de Preview-software beperkte mogelijkheden heeft of andere standaarden heeft op het gebied van beveiliging, privacy, toegankelijkheid, beschikbaarheid en betrouwbaarheid ten opzichte commerciële software.  

 Gebruik de informatie in de meeste productvereisten de [ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). De volgende uitzonderingen zijn van toepassing op de Technical Preview-versies:  

-   Elke installatie blijft gedurende 90 dagen actief, daarna wordt deze inactief.  

-   Engels is de enige ondersteunde taal.


-   Alleen de volgende installatievlaggen (schakelopties) worden ondersteund:  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Wanneer u de technische preview van het service connection point is standaard ingesteld op de onlinemodus wanneer het wordt geïnstalleerd, biedt geen ondersteuning voor een wijziging in de offlinemodus.

-   Indien van toepassing zijn extra beperkingen of vereisten opgenomen met details voor elke specifieke versie van de Technical Preview  

-   Er is geen ondersteuning voor migratie naar of van deze preview-versie.  

-   Er is geen ondersteuning voor het upgraden naar deze preview-versie.  

-   Er is geen ondersteuning voor het upgraden naar een productieversie (huidige vertakking) vanuit deze preview-versie. Echter, wanneer updates beschikbaar voor een preview-versie zijn, kunt u vinden en installeren uit de **Updates en onderhoud** knooppunt van de Configuration Manager-console. Zie [ConfigMgr-updatepakketten installeren](https://www.youtube.com/embed/KBd_EGFbUT8) op youtube.com voor een video van het upgradeproces in de console.  
-   Alleen zelfstandige primaire sites worden ondersteund. Er is geen ondersteuning voor centrale beheersites, meerdere primaire sites en secundaire sites.  

De volgende producten en technologieën worden ondersteund door deze vertakking van Configuration Manager. Ze zijn opgenomen in deze inhoud betekent echter niet dat een uitbreiding van ondersteuning voor een product of een versie die is levenscyclus van dat product afzonderlijke ondersteuning. Producten waarvan de levenscyclus van de ondersteuning worden niet ondersteund voor gebruik met Configuration Manager. Ga naar de website [Microsoft Support Lifecycle](http://go.microsoft.com/fwlink/p/?LinkId=208270) voor meer informatie over Microsoft Support-levenscycli.  

-   Alleen de volgende versies van SQL Server worden ondersteund:  

    -   SQL Server 2016 (zonder servicepack en hoger)
    -   SQL Server 2014 (met Service Pack 1 of hoger)
    -   SQL Server 2012 (met Service Pack 3 of hoger)


-   De site ondersteunt maximaal 10 clients waarop een van de volgende besturingssystemen moet worden uitgevoerd:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> De Technical Preview installeren en bijwerken  
 De System Center Configuration Manager Technical Preview is verschillend van de huidige release van System Center Configuration Manager.  

 Als u de Technical Preview wilt gebruiken, moet u eerst een **basislijnversie** van de Technical Preview-build installeren. Wanneer u een basislijnversie hebt geïnstalleerd, gebruikt u **in-console updates** om de installatie bij te werken naar de meest recente preview-versie. Normaal gesproken wordt er elke maand een nieuwe versie van de Technical Preview beschikbaar.

Elke preview-versie wordt ondersteund totdat drie opeenvolgende versies beschikbaar zijn. Dit betekent dat als versie 1708 versies, versie 1704 zou niet langer worden ondersteund, maar versie 1705, 1706 en 1707 in de ondersteuning blijft. Wanneer u een basislijn valt buiten het ondersteuning (zoals versie 1703), is het nog steeds ondersteund voor het installeren van een nieuwe technische Preview-site totdat een nieuwe basislijnversie beschikbaar, is zolang u die installatie naar een ondersteunde versie bijwerken. Bij het bijwerken, als u de meest recente versie die beschikbaar zijn in de console niet ziet, is bijgewerkt naar de meest recente versie aangeboden en Herhaal dit proces totdat u de meest recente versie van de technical preview kunt installeren.

> [!TIP]  
>  Wanneer u een update installeert voor de Technical Preview, werkt u de preview-installatie bij naar die nieuwe Technische Preview-versie.    De installatie van een preview-versie biedt nooit de optie voor het bijwerken naar een Current Branch-installatie of het ontvangen van updates van de Current Branch-release.  

**Basislijnversies van de Technical Preview activeren:**  
U kunt een basislijnversie gedurende maximaal 1 jaar na de release installeren. Wanneer u een nieuwe technische preview-site installeert, is het echter aangeraden te gebruiken van de meest recente basislijnversie die beschikbaar is.
-  **Technische Preview 1711** -de Configuration Manager Technical Preview 1711 is beschikbaar als zowel een in de console-update voor de Configuration Manager Technical Preview en als nieuwe basislijnversie die [beschikbaar via de TechNet Evaluation Center website](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).
-  **Technische Preview 1703** -de Configuration Manager Technical Preview 1703 is beschikbaar als zowel een in de console-update voor de Configuration Manager Technical Preview en als basislijnversie. Als u een nieuwe basislijn installeert, raden wij dat u versie 1711 gebruiken.


##  <a name="BKMK_TPFeedback"></a> Feedback geven  
 Feedback over onze Technical Previews is altijd welkom. Als u feedback wilt geven over de mogelijkheden van elke Preview, volgt u de koppeling naar ons feedbackformulier op de pagina voor het [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) op de Microsoft Connect-site.  

 En als u ideeën hebt over nieuwe functies die u graag zou zien, kunt u daar ook melding van maken. Als u nieuwe ideeën wilt indienen en wilt stemmen over de ideeën die door anderen zijn ingediend, gaat u naar onze [UserVoice-pagina](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a>Mogelijkheden die in de meest recente technical preview  
Hieronder vindt u de mogelijkheden die in elke technical preview-versie van Configuration Manager.  Mogelijkheden die beschikbaar zijn vanaf een bepaalde versie van de Technical Preview blijven beschikbaar in latere versies. Evenzo blijven mogelijkheden die zijn toegevoegd aan de Release voor System Center Configuration Manager (huidige vertakking) beschikbaar in volgende technical previews.  Klik verder naar de inhoud voor elke preview-versie voor meer informatie over een specifieke functie.  

 |Mogelijkheid |Technische Preview-versie |Huidige versie van het filiaal|  
 |----------------|---------------------|--------------------|
 |Verbeteringen in de takenreeksstap wordt uitgevoerd<!-- 1261338 --> | [Technische Preview 1711](capabilities-in-technical-preview-1711.md) |![Niet toegevoegd](media/Red_X.gif)    |
 |Interactie van de gebruiker toestaan bij het installeren van een toepassing<!-- 1356976 --> | [Technische Preview 1711](capabilities-in-technical-preview-1711.md) |![Niet toegevoegd](media/Red_X.gif)    |
 |Nieuwe beleidsregels voor nalevingsbeleid voor Windows 10<!-- 1356976 --> | [Technische Preview 1711](capabilities-in-technical-preview-1711.md#new-compliance-policy-options-for-windows-10) |![Niet toegevoegd](media/Red_X.gif)    |


## <a name="capabilities-delivered-in-previous-technical-previews"></a>Mogelijkheden die in vorige technical Previews worden geboden
 Wanneer alle functies van een technisch proefversie beschikbaar in de minimaal ondersteunde versie van de huidige vertakking zijn, worden de details voor deze preview-versie verwijderd uit de volgende tabel.  

 |Mogelijkheid |Technische Preview-versie |Huidige versie van het filiaal|  
 |----------------|---------------------|--------------------|
 |Windows 10-telemetrie voor Windows Analytics Apparaatstatus<!--1356148 --> | [Technische Preview 1710](capabilities-in-technical-preview-1710.md#limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health) |![Niet toegevoegd](media/Red_X.gif)    |
 |Verbeteringen voor pictogrammen voor Software Center<!-- 1356194 --> | [Technische Preview 1710](capabilities-in-technical-preview-1710.md#software-center-no-longer-distorts-icons-larger-than-250x250) |![Niet toegevoegd](media/Red_X.gif)    |
 |Controleren op naleving van Software Center voor naast beheerde apparaten<!-- 1356374 -->|[Technische Preview 1710](capabilities-in-technical-preview-1710.md#check-compliance-from-software-center-for-co-managed-devices)|![Niet toegevoegd](media/Red_X.gif)    |
 |Beperkte ondersteuning voor CNG-certificaten<!-- 1356191 -->| [Technische Preview 1710](capabilities-in-technical-preview-1710.md#limited-support-for-cng-certificates)|![Niet toegevoegd](media/Red_X.gif)    |
 |Ondersteuning voor misbruik Guard<!--1355468 --> | [Technische Preview 1710](capabilities-in-technical-preview-1710.md#support-for-exploit-guard) |[Versie 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)    |
 |Verbeterde beschrijvingen van in afwachting van opnieuw opstarten<!-- 1356283  -->| [Technische Preview 1710](capabilities-in-technical-preview-1710.md)|[Versie 1710](/sccm/core/clients/manage/manage-clients)    |
 |Device Guard beleidswijzigingen<!-- 1355092  -->| [Technische Preview 1710](capabilities-in-technical-preview-1710.md)|[Versie 1710](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)    |
 |Windows Defender toepassing Guard beleid configureren en implementeren<!-- 1351960  -->| [Technische Preview 1710](capabilities-in-technical-preview-1710.md)|[Versie 1710](/sccm/protect/deploy-use/create-deploy-application-guard-policy)    |
 |Verbeteringen voor het implementeren van PowerShell-scripts uit Configuration Manager<!-- 1236459 -->| [Technische Preview 1710](capabilities-in-technical-preview-1710.md#improvements-for-deploying-powershell-scripts-from-configuration-manager) | [Versie 1710](/sccm/apps/deploy-use/create-deploy-scripts)

## <a name="capabilities-delivered-in-previous-technical-previews"></a>Mogelijkheden die in vorige technical Previews worden geboden
 Wanneer alle functies van een technisch proefversie beschikbaar in de minimaal ondersteunde versie van de huidige vertakking zijn, worden de details voor deze preview-versie verwijderd uit de volgende tabel.  

 |Mogelijkheid |Technische Preview-versie |Huidige versie van het filiaal|  
 |----------------|---------------------|--------------------|
 |Verbeterde VPN-profiel ervaring in Configuration Manager-Console<!-- 1313282 --> | [Technische Preview 1709](capabilities-in-technical-preview-1709.md) |![Niet toegevoegd](media/Red_X.gif)    |
 |CO-beheer voor Windows 10-apparaten|[Technische Preview 1709](capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices)|[Versie 1710](/sccm/core/clients/manage/co-management-overview.md)|
 |Verbeteringen voor de scriptparameters op te geven wanneer u een PowerShell-scripts uit Configuration Manager implementeren<!-- 1236459 -->|[Technische Preview 1708](capabilities-in-technical-preview-1708.md#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|[Versie 1710](/sccm/apps/deploy-use/create-deploy-scripts)|
 |Management insights<!-- 1353967 --> |[Technische Preview 1708](capabilities-in-technical-preview-1708.md#management-insights)|![Niet toegevoegd](media/Red_X.gif)|
 |Computers uit de Configuration Manager-console opnieuw opstarten<!-- 1356283 --> |[Technische Preview 1708](capabilities-in-technical-preview-1708.md#restart-computers-from-the-configuration-manager-console)|[Versie 1710](/sccm/core/clients/manage/manage-clients) |
 |Aanpassing van software Center<!-- 1351224 --> |[Technische Preview 1708](capabilities-in-technical-preview-1708.md#software-center-customization)|![Niet toegevoegd](media/Red_X.gif)|
|Client-Peer-Cache-ondersteuning voor bestanden voor snelle installatie voor Windows 10 en Office 365|[Technische Preview 1707](capabilities-in-technical-preview-1707.md#client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365)|[Versie 1706](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache)|
 |Surface apparaat dashboard|[Technische Preview 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|![Niet toegevoegd](media/Red_X.gif)|
 |Windows Defender toepassing Guard beleid configureren en implementeren|[Technische Preview 1707](capabilities-in-technical-preview-1707.md#configure-and-deploy-windows-defender-application-guard-policies)|[Versie 1710](/sccm/protect/deploy-use/create-deploy-application-guard-policy)|
 |Parameters toevoegen bij het implementeren van PowerShell-scripts uit Configuration Manager|[Technische Preview 1707](capabilities-in-technical-preview-1707.md#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|[Versie 1710](/sccm/apps/deploy-use/create-deploy-scripts)|
 |Nieuwe beleidsinstellingen voor mobile application management|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#new-mobile-application-management-policy-settings)|[Versie 1710](/sccm/mdm/deploy-use/protect-apps-using-mam-policies#step-3-create-an-application-management-policy)|
 |Verbeterde grensgroepen voor software-updatepunten|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#improved-boundary-groups-for-software-update-points)|[Versie 1706](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)|
 |Beschikbaarheid van de site server-rol|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |![Niet toegevoegd](media/Red_X.gif)|
 |Vertrouwen voor specifieke bestanden en mappen in een beleid Device Guard opnemen|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#include-trust-for-specific-files-and-folders-in-a-device-guard-policy)|[Versie 1706](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|
 |Voortgang van de takenreeks verbergen|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#hide-task-sequence-progress)|![Niet toegevoegd](media/Red_X.gif)|
 |Geef een andere locatie van inhoud voor installatie-inhoud en inhoud verwijderen|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#specify-a-different-content-location-for-install-content-and-uninstall-content)|[Versie 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#hide-task-sequence-progress)|
 |Verbeterde toegankelijkheid |[Technische Preview 1706](capabilities-in-technical-preview-1706.md#accessibility-improvements)|[Versie 1706](/sccm/core/understand/accessibility-features)|
 |Ondersteuning van Azure Services Wizard gereedheid voor Upgrade |[Technische Preview 1706](capabilities-in-technical-preview-1706.md#changes-to-the-azure-services-wizard-to-support-upgrade-readiness)|[Versie 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Nieuwe clientinstellingen voor cloud-services|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#new-client-settings-for-cloud-services)|[Versie 1706](/sccm/core/clients/deploy/deploy-clients-cmg-azure)|
 |Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#create-and-run-powershell-scripts-from-the-configuration-manager-console)|[Versie 1710](/sccm/apps/deploy-use/create-deploy-scripts)|
 |Ondersteuning voor PXE-netwerk opstarten voor IPv6 |[Technische Preview 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|![Niet toegevoegd](media/Red_X.gif)|
 |Updates voor Microsoft Surface stuurprogramma's beheren |[Technische Preview 1706](capabilities-in-technical-preview-1706.md#manage-microsoft-surface-driver-updates)|[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#manage-microsoft-surface-driver-updates)|
 |Windows Update voor bedrijven uitgestelde beleid configureren |[Technische Preview 1706](capabilities-in-technical-preview-1706.md#configure-windows-update-for-business-deferral-policies)|[Versie 1706](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)|
 |iOS-inschrijving beperkingen|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[Versie 1706](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions)|
 |Beperkingen voor android-inschrijving|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[Versie 1706](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)|
 |Android for Work application management-beleid voor kopiëren en plakken|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#android-for-work-application-management-policy-for-copy-paste)|[Versie 1706](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client#android-for-work-configuration-item-settings-reference)|
 |Nieuwe configuratie-item-instellingen van Windows|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#new-windows-configuration-item-settings)|[Versie 1706](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Nieuwe beleidsregels voor naleving van apparaat|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#new-device-compliance-policy-rules)|[Versie 1706](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Apparaat Health Attestation beoordeling van van nalevingsbeleid voor voorwaardelijke toegang|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|![Niet toegevoegd](media/Red_X.gif)|
 |Ondersteuning voor Entrust certificeringsinstanties|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#support-for-entrust-certification-authorities)|[Versie 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Cisco (IPSec) ondersteuning voor Mac OS VPN-profielen|[Technische Preview 1706](capabilities-in-technical-preview-1706.md#cisco-ipsec-support-for-macos-vpn-profiles)|[Versie 1706](/sccm/protect/deploy-use/vpn-profiles)|
 |Nieuwe mogelijkheden voor Azure AD en in de cloud management|[Technische Preview 1705](capabilities-in-technical-preview-1705.md#new-capabilities-for-azure-ad-and-cloud-management)|[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#azure-ad-integration-with-configuration-manager)|
 |Windows Defender toepassing Guard beleid configureren en implementeren|[Technische Preview 1705](capabilities-in-technical-preview-1705.md#configure-and-deploy-windows-defender-application-guard-policies)|[Versie 1710](/sccm/protect/deploy-use/create-deploy-application-guard-policy)|
 |Hulpprogramma voor het bijwerken opnieuw instellen  |[Technische Preview 1705](capabilities-in-technical-preview-1705.md#update-reset-tool)|[Versie 1706](/sccm/core/servers/manage/update-reset-tool)|
 |Hoge DPI-ondersteuning  |[Technische Preview 1705](capabilities-in-technical-preview-1705.md#high-dpi-console-support)|[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#high-dpi-console-support)|
 |Verbeteringen voor peer-Cache  |[Technische Preview 1705](capabilities-in-technical-preview-1705.md#peer-cache-improvements) |[Versie 1706](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache)|
 |Verbeteringen voor SQL Server altijd op beschikbaarheidsgroepen |[Technische Preview 1705](capabilities-in-technical-preview-1705.md#improvements-for-sql-server-always-on-availability-groups) |[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#improvements-for-sql-server-always-on-availability-groups)|
 |Verbeterde berichten van de gebruiker voor Office 365-updates|[Technische Preview 1705](capabilities-in-technical-preview-1705.md#improved-user-notifications-for-office-365-updates) |[Versie 1706](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)|
 |Wizard Azure-Services gebruiken een verbinding met OMS configureren|[Technische Preview 1705](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms) |[Versie 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Android-apps met app-configuratiebeleid configureren  |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![Niet toegevoegd](media/Red_X.gif)|
 |Hardware-inventaris verzamelt gegevens van beveiligd opstarten |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#hardware-inventory-collects-secure-boot-information)|
 |Takenreeksen onderliggende toevoegen aan een takenreeks|[Technische Preview 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![Niet toegevoegd](media/Red_X.gif)|
 |Laden van installatiekopieën voor opstarten met huidige Windows PE-versie |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|[Versie 1706](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)|
 |Verbeteringen in de implementatie van besturingssysteem<!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![Niet toegevoegd](media/Red_X.gif)|
 |Volume-purchased iOS-apps implementeren op apparaatverzamelingen|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[Versie 1702](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |Directe koppelingen naar toepassingen in Software Center|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|[Versie 1706](/sccm/apps/deploy-use/share-applications)
 |PFX-certificaten voor Configuration Manager Windows-clientcomputers|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|[Versie 1706](/sccm/protect/deploy-use/create-certificate-profiles)|
 |Wizard Azure-Services configureren|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|[Versie 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Converteren van BIOS naar UEFI in een takenreeks voor besturingssysteem upgraden| [Technische Preview 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[Versie 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |Samenvouwbare takenreeksgroepen| [Technische Preview 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |[Versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#collapsible-task-sequence-groups)|
 |Clientinstellingen voor het configureren van Windows Analytics gereedheid voor Upgrade | [Technische Preview 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |[Versie 1706](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics)|
 |Nieuwe instellingen voor naleving voor iOS-apparaten|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[Versie 1702](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |PFX-certificaten te maken met S/MIME-ondersteuning|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[Versie 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[Versie 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Feedback verzenden vanuit de Configuration Manager-console | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |Wijzigingen voor Updates en onderhoud  | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |Verbeteringen voor peer-Cache  | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[Versie 1702](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Azure Active Directory gebruiken<!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![Niet toegevoegd](media/Red_X.gif)|
 |Voorwaardelijke toegang apparaat naleving beleid verbeteringen | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[Versie 1702](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Waarschuwing voor Antimalware client versie | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[Versie 1702](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Nalevingsbeoordeling voor Windows Update voor bedrijven-updates | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen aan Software Center-instellingen en meldingen voor hoge impact takenreeksen|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[Versie 1702](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android voor Work-ondersteuning| [Technische Preview 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[Versie 1702](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |Grens groepen verbeteringen voor software-updatepunten | [Technische Preview 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[Versie 1702](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |Hardware-inventaris verzamelt UEFI-informatie | [Technische Preview 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[Versie 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |Verbeteringen in de implementatie van besturingssysteem| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |Host software-updates op cloud-gebaseerde distributiepunten| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|[Versie 1702](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#plan-to-use-a-cloud-based-distribution-point) |
 |Apparaat health attestation-gegevens via beheerpunten valideren| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [Versie 1702](/sccm/core/servers/manage/health-attestation) |
 |OMS-connector voor Microsoft Azure Government cloud |[Technische Preview 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[Versie 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Android en iOS-versies worden niet meer targetable in wizards maken |[Technische Preview 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |
 |Toegang tot de gegevens van de OData-eindpunt |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![Niet toegevoegd](media/Red_X.gif)|
 |Datawarehouse-servicepunt |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[Versie 1702](/sccm/core/servers/manage/data-warehouse)|
 |Inhoudsbibliotheek opschoonprogramma |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[Versie 1702](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |Verbeteringen voor zoeken in de console |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |De installatie van een toepassing voorkomen als een opgegeven programma wordt uitgevoerd|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[Versie 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Nieuwe Windows Hello voor bedrijven kennisgeving voor eindgebruikers|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#new-windows-hello-for-business-notification-for-end-users)|
 |Windows Store voor bedrijven-ondersteuning in Configuration Manager|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|[Versie 1702](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Terug naar vorige pagina wanneer een takenreeks mislukt|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Snelle installatie bestanden ondersteuning voor Windows 10-updates|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[Versie 1702](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |De voorbereiding op Azure Active Directory|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|[Versie 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Wijzig bij het configureren van multi-factor authentication voor apparaatinschrijving|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![Niet toegevoegd](media/Red_X.gif)|
 |Vooraf cache-inhoud voor implementaties en takenreeksen |[Technische Preview 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[Versie 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |Configuratie-instellingen voor Windows Defender|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[Versie 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Aanvraag beleid synchroniseren vanuit de administrator-console|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[Versie 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |Ondersteuning voor extra beveiliging rol voor alle apparaten in Bedrijfseigendom knooppunt|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[Versie 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Voorwaardelijke toegang voor Windows 10 VPN-profielen|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[Versie 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |Filteren op Inhoudsgrootte in regels voor automatische implementatie|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[Versie 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |Verbeterde functionaliteit voor vereiste software-dialoogvensters|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[Versie 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Eerder goedgekeurde toepassingsaanvragen weigeren|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[Versie 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Clients uitsluiten van Automatische upgrade|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[Versie 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Verbeteringen in Endpoint Protection|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[Versie 1610](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |Toenemend aantal geregistreerde apparaten|[Technische Preview 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[Versie 1610](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |Aanvullende Apple DEP-instellingen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[Versie 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Verbeteringen in Windows Store voor bedrijven-integratie met Configuration Manager|[Technische Preview 1609](capabilities-in-technical-preview-1609.md)|[Versie 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Nieuwe instellingen voor naleving voor configuratie-items|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[Versie 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Integratie met de Upgrade Analytics|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[Versie 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Systeemeigen verbindingstypen voor Windows 10 hybride VPN-profielen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen voor grensgroepen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[Versie 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Dashboard voor Office 365-clientbeheer|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[Versie 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |Office 365-apps implementeren op clients|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[Versie 1702](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |Verbeteringen in BIOS in UEFI-conversie|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[Versie 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Intune naleving grafieken|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[Versie 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|


 <!--  TP 1608 and earlier have aged out of support. Features from these previews are either in the minimum supported Current Branch version, or are not scheduled for inclusion.
 |Improvements to the Prepare ConfigMgr Client for Capture task sequence step|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[Version 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |Improvements to Software Center|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[Version 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Improvements to Asset Intelligence|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|N/A|
 |Remote control keyboard translation|[Tech Preview 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|[Version 1702](/sccm/core/clients/manage/remote-control/configuring-remote-control#enable-keyboard-translation)|
 |Improvements to the Windows 10 Edition Upgrade Policy|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[Version 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Customizable Branding for Software Center Dialogs|[Tech Preview 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|[Version 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#customizable-branding-for-software-center-dialogs)|  
 |Multiple device management points for On-premises Mobile Device Management|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Automatically categorize devices into collections|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[Version 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Enforcement grace period for required application and software update deployments|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[Version 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Using Configuration Manager as a Managed Installer with Device Guard|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|[Version 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|
 |Cloud management gateway (formerly Cloud Proxy Service)|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [Version 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Manage the Office 365 client agent in Configuration Manager|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |The OSDPreserveDriveLetter task sequence variable has been deprecated|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[Version 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |Changes for the Updates and Servicing Node|[Tech Preview 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Per-app VPN for Windows 10 devices|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[Version 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |Improvements to the Install software updates task sequence|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |Improvements to the Prepare ConfigMgr Client for Capture task sequence step |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[Version 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Grace period for required application deployments |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|N/A|  
 |New experience for remote device actions |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Windows Store for Business apps |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[Version 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |General improvements for volume-purchased apps|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Enterprise Data Protection (EDP)|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |End users can install apps from the Company Portal |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|N/A|  
 |New tabs for Updates and Operating Systems in Software Center|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[Version 1606 ](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Service a server group |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[Version 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Support for Windows Defender Advanced Threat Protection service |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[Version 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |New restart options for Windows 10 clients after software update installation|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[Version 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |On-premises Device Health Attestation |[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[Version 1606](/sccm/core/servers/manage/health-attestation)|  
 |Pre-declare corporate-owned devices with IMEI or iOS serial number|[Tech Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[Version 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |Manage volume-purchased apps from the Windows Store for Business| [Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[Version 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Improvements to Microsoft Passport for Work management|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Option for clients to switch to a new software update point|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[Version 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Client settings to manage Client Cache Settings and client Peer Cache |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Client Settings: [Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Peer Cache: [Version 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |Support for Passport for Work as a KSP |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[Version 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |On-premises Device Health Attestation|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[Version 1606](/sccm/core/servers/manage/health-attestation)|  
 |SmartLock setting for Android devices|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[Version 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->



## <a name="see-also"></a>Zie ook  
[Wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Inleiding op System Center Configuration Manager](../../core/understand/introduction.md)
