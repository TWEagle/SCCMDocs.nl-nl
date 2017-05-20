---
title: Technische Preview van System Center Configuration Manager | Microsoft-documenten
description: Meer informatie over de technische voorbeeldversie dat we u Maak een proefrit met nieuwe functies en mogelijkheden in System Center Configuration Manager.
ms.custom: na
ms.date: 4/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 3a7370fedee417588d219dc7bff46205faf42929
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Technical Preview voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

**Welkom bij de evaluatieversie van System Center Configuration Manager technische**. Dit onderwerp bevat informatie over de preview-versie die in ontwikkeling is en die nieuwe functionaliteit en mogelijkheden introduceert waaraan wij werken. Bij elke versie van de technische preview, worden nieuwe functies die niet zijn opgenomen in de huidige vertakking van System Center Configuration Manager op het moment dat de technische voorbeeldversie beschikbaar wordt gesteld geïntroduceerd. Deze functies worden uiteindelijk misschien opgenomen in een update van de huidige release, maar voordat we de functies voltooien en toevoegen, willen we u de mogelijkheid bieden ze uit te proberen en ons feedback te geven.  

 Omdat dit een Technical Preview is, kan het zijn dat de details en functionaliteit nog worden gewijzigd.  

 In dit onderwerp bevat informatie die geldt voor alle versies van de technische Preview en ook een lijst met elke nieuwe capaciteit (of functie) samen met de technische voorbeeldversie waarin de mogelijkheid wordt eerst, zoals versie 1701 voor januari van 2017 weergegeven. De details van deze mogelijkheden worden per preview-versie in afzonderlijke onderwerpen beschreven.  

 Zie voor meer informatie over wat er nieuw in de huidige vertakking van Configuration Manager [wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Voorwaarden en beperkingen voor de Technical Preview  

> [!IMPORTANT]     
>  Een licentie voor een Technical Preview wordt alleen gegeven voor gebruik in een testomgeving.  Microsoft biedt wellicht geen ondersteuningsdiensten en bepaalde functies zijn mogelijk niet beschikbaar in de Preview-software. Daarnaast is het mogelijk dat de Preview-software beperkte mogelijkheden heeft of andere standaarden heeft op het gebied van beveiliging, privacy, toegankelijkheid, beschikbaarheid en betrouwbaarheid ten opzichte commerciële software.  

 Gebruik de informatie in voor de meeste product vereisten, de [ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). De volgende uitzonderingen zijn van toepassing op de Technical Preview-versies:  

-   Elke installatie blijft gedurende 90 dagen actief, daarna wordt deze inactief.  

-   Engels is de enige ondersteunde taal.


-   Alleen de volgende installatievlaggen (schakelopties) worden ondersteund:  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Standaard, wanneer u de technische preview is de service connection point ingesteld op onlinemodus wanneer deze wordt geïnstalleerd en biedt geen ondersteuning voor een wijziging in de offline modus.

-   Indien van toepassing zijn extra beperkingen of vereisten opgenomen met details voor elke specifieke versie van de Technical Preview  

-   Er is geen ondersteuning voor migratie naar of van deze preview-versie.  

-   Er is geen ondersteuning voor het upgraden naar deze preview-versie.  

-   Er is geen ondersteuning voor het upgraden naar een productieversie (huidige vertakking) vanuit deze preview-versie. Echter, wanneer er updates beschikbaar zijn voor een preview-versie, kunt u zoeken en installeren van de **Updates en onderhoud** knooppunt van de Configuration Manager-console. Zie [ConfigMgr-updatepakketten installeren](https://www.youtube.com/embed/KBd_EGFbUT8) op youtube.com voor een video van het upgradeproces in de console.  
-   Alleen zelfstandige primaire sites worden ondersteund. Er is geen ondersteuning voor centrale beheersites, meerdere primaire sites en secundaire sites.  

De volgende producten en technologieën worden ondersteund door de vertakking van Configuration Manager. Ze zijn opgenomen in deze inhoud impliceert een uitbreiding van ondersteuning voor een product of de versie die boven dat product afzonderlijke support lifecycle echter niet. Producten die zich buiten de levenscyclus van de ondersteuning worden niet ondersteund voor gebruik met Configuration Manager. Ga naar de website [Microsoft Support Lifecycle](http://go.microsoft.com/fwlink/p/?LinkId=208270) voor meer informatie over Microsoft Support-levenscycli.  

-   Alleen de volgende versies van SQL Server worden ondersteund:  

    -   SQL Server 2016 (zonder servicepack of hoger)
    -   SQL Server 2014 (met Service Pack 1 of hoger)
    -   SQL Server 2012 (met Service Pack 3 of hoger)


-   De site ondersteunt maximaal 10 clients waarop een van de volgende besturingssystemen moet worden uitgevoerd:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> De Technical Preview installeren en bijwerken  
 De System Center Configuration Manager Technical Preview verschilt van de huidige release van System Center Configuration Manager.  

 Als u de Technical Preview wilt gebruiken, moet u eerst een **basislijnversie** van de Technical Preview-build installeren. Wanneer u een basislijnversie hebt geïnstalleerd, gebruikt u **in-console updates** om de installatie bij te werken naar de meest recente preview-versie.     Normaal gesproken wordt er elke maand een nieuwe versie van de Technical Preview beschikbaar.

Elke preview-versie wordt ondersteund totdat drie opeenvolgende releases beschikbaar zijn. Wat betekent dat wanneer versie 1702 worden vrijgegeven, versie 1610 zou niet langer ondersteund, maar versies 1611 1612 en 1701 ondersteund blijft. Wanneer een basislijn valt buiten-ondersteuning (zoals versie 1610), is het nog steeds ondersteund voor het installeren van een nieuwe technische Preview van site tot een nieuwe versie van de basislijn beschikbaar is, zolang u die installatie naar een ondersteunde versie bijwerken. Wanneer u bijwerkt, als u de meest recente versie die beschikbaar zijn in de console niet ziet, update naar de nieuwste versie aangeboden en Herhaal dit proces totdat u de meest recente versie van de technische preview kunt installeren.

> [!TIP]  
>  Wanneer u een update installeert voor de Technical Preview, werkt u de preview-installatie bij naar die nieuwe Technische Preview-versie.    De installatie van een preview-versie biedt nooit de optie voor het bijwerken naar een Current Branch-installatie of het ontvangen van updates van de Current Branch-release.  

**Basislijnversies van de Technical Preview activeren:**  
U kunt een basislijn versie installeren voor tot 1 jaar na de release. Echter, als u een nieuwe technische preview-site installeert, raden wij aan u de meest recente versie van basislijn die beschikbaar is.
-  **Technische Preview 1703** -de Configuration Manager technische Preview 1703 is beschikbaar als zowel een console update voor de Configuration Manager Technical Preview en als een nieuwe basislijn-versie die beschikbaar is in de TechNet-Evaluatiecentrum-website.

-  **Technische Preview 1610** -de Configuration Manager technische Preview 1610 is beschikbaar als zowel een console update voor de Configuration Manager Technical Preview en als de versie van een basislijn. Als u media voor het installeren van 1610 hebt, raden wij u versie 1703 versie downloaden en installeren die in plaats daarvan.




##  <a name="BKMK_TPFeedback"></a> Feedback geven  
 Feedback over onze Technical Previews is altijd welkom. Als u feedback wilt geven over de mogelijkheden van elke Preview, volgt u de koppeling naar ons feedbackformulier op de pagina voor het [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) op de Microsoft Connect-site.  

 En als u ideeën hebt over nieuwe functies die u graag zou zien, kunt u daar ook melding van maken. Als u nieuwe ideeën wilt indienen en wilt stemmen over de ideeën die door anderen zijn ingediend, gaat u naar onze [UserVoice-pagina](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Mogelijkheden die in Technical Previews worden geboden  
 Hier volgen de mogelijkheden die wordt geleverd met elke technische voorbeeldversie van Configuration Manager.  Mogelijkheden die beschikbaar zijn vanaf een bepaalde versie van de Technical Preview blijven beschikbaar in latere versies. Op deze manier blijven mogelijkheden die zijn toegevoegd aan de Release voor System Center Configuration Manager (huidige vertakking) in de volgende technische voorbeelden beschikbaar.  Klik verder naar de inhoud voor elke preview-versie voor meer informatie over een specifieke functie.  

 |Mogelijkheid |Technische Preview-versie |Huidige versie van het filiaal|  
|----------------|---------------------|--------------------|
 |Android-apps configureren met app-configuratiebeleid  |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![Niet toegevoegd](media/Red_X.gif)|
 |Hardware-inventaris verzamelt informatie beveiligd opstarten |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|![Niet toegevoegd](media/Red_X.gif)|
 |Onderliggende takenreeksen toevoegen aan een takenreeks|[Technische Preview 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![Niet toegevoegd](media/Red_X.gif)|
 |Laden van installatiekopieën voor opstarten met huidige Windows PE-versie |[Technische Preview 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen in de implementatie van besturingssysteem|[Technische Preview 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![Niet toegevoegd](media/Red_X.gif)|
 |Volume aangeschaft iOS-apps implementeren op apparaatverzamelingen|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[Versie 1702](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |Directe koppelingen naar toepassingen in Software Center|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|![Niet toegevoegd](media/Red_X.gif)
 |PFX-certificaten voor Configuration Manager Windows client-computers|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|![Niet toegevoegd](media/Red_X.gif)|
 |Wizard Azure-Services configureren|[Technische Preview 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|![Niet toegevoegd](media/Red_X.gif)|
 |Omzetten van BIOS UEFI in een takenreeks voor de upgrade van besturingssysteem| [Technische Preview 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[Versie 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |Samenvouwbare takenreeksgroepen| [Technische Preview 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |![Niet toegevoegd](media/Red_X.gif)|
 |Clientinstellingen voor het configureren van Windows Analytics voor gereedheid voor Upgrade | [Technische Preview 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |![Niet toegevoegd](media/Red_X.gif)|
 |Nieuwe compatibiliteitsinstellingen voor iOS-apparaten|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[Versie 1702](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |PFX-certificaten te maken met S/MIME-ondersteuning|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[Versie 1702](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Controleer voor het uitvoeren van uitvoerbare bestanden voordat de installatie van een toepassing|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[Versie 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Feedback verzenden vanuit de Configuration Manager-console | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |Wijzigingen voor Updates en onderhoud  | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |Peer-Cache verbeteringen  | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[Versie 1702](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Gebruik Azure Active Directory  | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![Niet toegevoegd](media/Red_X.gif)|
 |Voorwaardelijke toegang apparaat naleving beleid verbeteringen | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[Versie 1702](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Waarschuwing voor Antimalware client-versie | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[Versie 1702](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Beoordeling van naleving voor Windows Update voor Business-updates | [Technische Preview 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen in Software Center-instellingen en meldingen voor indrukwekkende takenreeksen|[Technische Preview 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[Versie 1702](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android voor ondersteuning van werkitems| [Technische Preview 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[Versie 1702](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |Grens groepen verbeteringen voor software-updatepunten | [Technische Preview 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[Versie 1702](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |Hardware-inventaris verzamelt informatie UEFI | [Technische Preview 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[Versie 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |Verbeteringen in de implementatie van besturingssysteem| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |Host-software-updates op cloud-gebaseerde distributiepunten| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|![Niet toegevoegd](media/Red_X.gif) |
 |Status attestation apparaatgegevens via beheerpunten valideren| [Technische Preview 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [Versie 1702](/sccm/core/servers/manage/health-attestation) |
 |OMS connector voor de overheid van de Microsoft Azure-cloud |[Technische Preview 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[Versie 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Android en iOS-versies zijn niet langer in wizards voor het maken van targetable |[Technische Preview 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |![Niet toegevoegd](media/Red_X.gif) |
 |Toegang tot de gegevens van de OData-eindpunt |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![Niet toegevoegd](media/Red_X.gif)|
 |Gegevenspunt-Service datawarehouse |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[Versie 1702](/sccm/core/servers/manage/data-warehouse)|
 |Inhoudsbibliotheek-hulpprogramma |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[Versie 1702](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |Verbeteringen voor de zoekopdracht console |[Technische Preview 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |Voorkomen dat de installatie van een toepassing als een opgegeven programma wordt uitgevoerd|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[Versie 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Nieuwe Windows Hello voor zakelijke kennisgeving voor eindgebruikers|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|![Niet toegevoegd](media/Red_X.gif)|
 |Windows Store voor Business-ondersteuning in Configuration Manager|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|![Niet toegevoegd](media/Red_X.gif)|
 |Teruggaan naar vorige pagina wanneer een takenreeks mislukt|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[Versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Snelle installatie bestanden ondersteuning voor Windows 10-updates|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[Versie 1702](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |Azure Active Directory voorbereiden|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|![Niet toegevoegd](media/Red_X.gif)|
 |Wijzig in configureren multi-factor authentication voor apparaatinschrijving|[Technische Preview 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![Niet toegevoegd](media/Red_X.gif)|
 |Vooraf cache-inhoud voor implementaties en takenreeksen |[Technische Preview 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[Versie 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |Configuratie-instellingen voor Windows Defender|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[Versie 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Aanvraag beleid synchronisatie van de administrator-console|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[Versie 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |Ondersteuning voor extra beveiliging rol voor alle apparaten in Bedrijfseigendom knooppunt|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[Versie 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Voorwaardelijke toegang voor Windows 10 VPN-profielen|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[Versie 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |Filteren op de omvang van de inhoud in de regels voor automatische implementatie|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[Versie 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |Verbeterde functionaliteit voor vereiste software dialoogvensters|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[Versie 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Eerder goedgekeurde toepassingsaanvragen weigeren|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[Versie 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Clients uitsluiten voor automatische upgrade|[Technische Preview 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[Versie 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Verbeteringen in de Endpoint Protection|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[Versie 1610](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |Toenemend aantal geregistreerde apparaten|[Technische Preview 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[Versie 1610](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |Aanvullende Apple DEP-instellingen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[Versie 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Uitbreidingen voor Windows Store voor Business-integratie met Configuration Manager|[Technische Preview 1609](capabilities-in-technical-preview-1609.md)|[Versie 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Nieuwe compatibiliteitsinstellingen voor configuratie-items|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[Versie 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Integratie met de Upgrade Analytics|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[Versie 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Systeemeigen verbindingstypen voor Windows 10 hybride VPN-profielen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen voor grensgroepen|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[Versie 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Office 365 clientbeheer dashboard|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[Versie 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |Office 365-apps implementeren op clients|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[Versie 1702](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |Verbeteringen in BIOS UEFI-conversie|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[Versie 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Intune compatibiliteit grafieken|[Technische Preview 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[Versie 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|
 |Verbeteringen in de takenreeksstap ConfigMgr-client voorbereiden voor vastleggen|[Technische Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[Versie 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |Verbeteringen in Software Center|[Technische Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[Versie 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Verbeteringen in de Asset Intelligence|[Technische Preview 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|![Niet toegevoegd](media/Red_X.gif)|
 |Beheer op afstand toetsenbord vertaling|[Technische Preview 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|![Niet toegevoegd](media/Red_X.gif)|
 |Verbeteringen in het upgradebeleid van de Windows 10-editie|[Technische Preview 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[Versie 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Aanpasbare huisstijl voor Software Center-dialoogvensters|[Technische Preview 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|![Niet toegevoegd](media/Red_X.gif)|  
 |Meerdere apparaatbeheerpunten voor On-premises Mobile Device Management|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Apparaten automatisch categoriseren in verzamelingen|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[Versie 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Respijtperiode afdwingen voor vereiste toepassingen en software-update-implementaties|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[Versie 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Configuration Manager gebruiken als een beheerd installatieprogramma met Device Guard|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|![Niet toegevoegd](media/Red_X.gif)|
 |Cloud management gateway (voorheen Proxy Cloudservice)|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [Versie 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Office 365-clientagent beheren in Configuration Manager|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |Takenreeksvariabele OSDPreserveDriveLetter is afgeschaft|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[Versie 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |Wijzigingen voor het knooppunt Updates en onderhoud|[Technische Preview 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Per app VPN voor Windows 10-apparaten|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[Versie 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |Verbeteringen in de takenreeks Software-updates installeren|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |Verbeteringen in de takenreeksstap ConfigMgr-client voorbereiden voor vastleggen |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[Versie 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Respijtperiode voor vereiste toepassingsimplementaties |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|![Niet toegevoegd](media/Red_X.gif)|  
 |Nieuwe ervaring voor acties van externe apparaten |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Windows Store voor Bedrijven-apps |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[Versie 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Algemene verbeteringen voor apps die zijn gekocht via het volume-aankoopprogramma|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Ondernemingsgegevensbescherming (EDP)|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Eindgebruikers kunnen apps installeren vanuit de bedrijfsportal |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|![Niet toegevoegd](media/Red_X.gif)|  
 |Nieuwe tabbladen voor Updates en Besturingssystemen in Software Center|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Een servergroep onderhouden |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[Versie 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Ondersteuning voor de Windows Defender-service Advanced Threat Protection |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[Versie 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |Nieuwe opties voor het opnieuw opstarten van Windows 10-clients na de installatie van een software-update|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[Versie 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |On-premises apparaatstatusverklaring |[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[Versie 1606](/sccm/core/servers/manage/health-attestation)|  
 |Vooraf declareren van apparaten in bedrijfseigendom met IMEI-nummer of iOS-serienummer|[Technische Preview 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[Versie 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |Apps die zijn gekocht via het volume-aankoopprogramma beheren via de Windows Store voor Bedrijven| [Technische Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[Versie 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Verbeteringen in Microsoft Passport voor Work-beheer|[Technische Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Optie voor clients om over te schakelen op een nieuw software-updatepunt|[Technische Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[Versie 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Clientinstellingen voor het beheren van de clientcache-instellingen en client-peer-cache |[Technische Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Clientinstellingen: [Versie 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Peercache: [Versie 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |Ondersteuning voor Passport for Work als een sleutelarchiefprovider (KSP) |[Technische Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[Versie 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |On-premises apparaatstatusverklaring|[Technische Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[Versie 1606](/sccm/core/servers/manage/health-attestation)|  
 |SmartLock-instelling voor Android-apparaten|[Technische Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[Versie 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 <!--  TP 1603 Aged out of support and all features in Current Branch Builds:
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->
 Wanneer alle functies van technische voorbeeldversie beschikbaar in de minimaal ondersteunde versie van de huidige vertakking wordt weergegeven zijn, worden de details voor deze preview-versie verwijderd uit deze tabel.


## <a name="see-also"></a>Zie ook  
[Wat is er nieuw in System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Inleiding tot System Center Configuration Manager](../../core/understand/introduction.md)

